# Rollback Notes

## Ce s-a intamplat
Am simulat un incident modificand portul din Procfile de la 5000 la 9999.

## Cum am detectat problema
Pipeline-ul a rulat deploy pe staging, dar health check-ul a picat.
Aplicatia nu raspundea corect, iar job-ul healthcheck_staging a dat fail.

## Impact
Deploy-ul nu a mai continuat spre production.
Astfel am evitat sa public o versiune defecta.

## Ce am facut pentru rollback
Am revenit la configuratia corecta din Procfile, folosind portul 5000.
Apoi am dat commit si push din nou.

## Rezultat
Pipeline-ul a trecut cu succes:
staging ok
approval
production ok
health check ok

Asa poti opri un release defect inainte sa ajunga in productie si poti face rollback rapid.
