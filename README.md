# lab-7
# 📱Android Dynamic Analysis with MobSF & DIVA

Ce dépôt documente la mise en place d'un laboratoire de test d'intrusion mobile dédié à l'**analyse dynamique (runtime)** d'applications Android. L'objectif est d'exploiter la plateforme **DIVA** (*Damn Insecure and Vulnerable Application*) à l'aide du framework automatisé **MobSF** (*Mobile Security Framework*) pour identifier des vulnérabilités en temps réel.

---

##  Objectifs du Laboratoire
* **Maîtrise du Runtime :** Comprendre le comportement d'un APK à l'exécution (fichiers créés, processus, flux).
* **Interception et Audit :** Capturer le trafic réseau chiffré (HTTPS) et inspecter les logs système en direct.
* **Détection de Vulnérabilités :** Identifier des failles critiques (stockage non sécurisé, fuites de logs, secrets hard-coded, mauvaise configuration d'Intents).
* **Automatisation :** Utiliser la puissance de MobSF couplée à Frida pour orchestrer l'analyse.

---

##  Architecture du Laboratoire

```text
[ Docker: MobSF ] <---> [ Proxy Interception ] <---> [ AVD (Android API 30) ]
                              (HTTPS)                     (DIVA APK + Frida)
```
<img width="688" height="412" alt="11" src="https://github.com/user-attachments/assets/65a04c2c-d487-49b3-b098-5b419401a154" />

## Étape 3 : Lancement de MobSF via Docker Dans un nouveau terminal (l’émulateur doit tourner) :

bash docker run -it --rm -p 8000:8000 --network=host -e MOBSF_ANALYZER_IDENTIFIER=emulator-5554 opensecurity/mobile-security-framework-mobsf:latest

<img width="715" height="327" alt="2" src="https://github.com/user-attachments/assets/fc24872e-c1b2-4f43-8218-51dd8aea7b8a" />

## Étape 4 : Accès à l’interface MobSF Ouvrir le navigateur : http://127.0.0.1:8000

Identifiant : mobsf

Mot de passe : mobsf

<img width="507" height="335" alt="3" src="https://github.com/user-attachments/assets/e66e4e37-f01d-4e28-a40c-41543d5fdec3" />

## Étape 5 : Téléchargement de l’APK DIVA Cloner le dépôt DIVA :

<img width="590" height="186" alt="4" src="https://github.com/user-attachments/assets/c6a71155-7f36-4820-a6e5-7d0bd02883df" />

## Étape 6 : Upload et analyse statique Dans MobSF :

Cliquer sur Upload & Analyze.

Sélectionner le fichier diva-beta.apk.

Attendre la fin de l’analyse statique (scores, permissions, manifests).

<img width="631" height="465" alt="5" src="https://github.com/user-attachments/assets/282e7df4-c762-4533-b60b-c08a04fadbc0" />


<img width="678" height="342" alt="6" src="https://github.com/user-attachments/assets/7bcf5bfc-836c-47bc-b275-2f5d32180eff" />

## Étape 7 : Lancement de l’analyse dynamique Dans le rapport statique :

<img width="1040" height="241" alt="7" src="https://github.com/user-attachments/assets/f02635d7-3816-48bc-a96f-b3c9afe0fcc0" />
<img width="907" height="497" alt="8" src="https://github.com/user-attachments/assets/af9145b6-e763-4c5e-bced-b1ce082d4efb" />
<img width="360" height="510" alt="9" src="https://github.com/user-attachments/assets/e53dcce1-1d06-4a07-a3b5-b391744b17e0" />
