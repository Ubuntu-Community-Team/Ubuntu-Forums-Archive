---
title: "[SOLVED] JDownloader - wrong java version"
date: 2008-11-19
forum: General Help
---

### Post by sambita on 2008-11-19
Hello, i used to be able to run JDownloader with no problems in Hardy Heron, but i've recently installed Intrepid and since then im unable to use it. There seems to be a problem with my java version, although everything else(java-related) works well. I get this message when trying to run JDownloader:
 
You useses a wrong Java version. Please use a original Sun Java. Start jDownloader anyway?
Your Java Version:
Runtime Name
icedtea6 1.3.1 (6b12-0ubuntu6) runtime environment
Runtime Version
1.6.0_0-b12

Does anyone know what can i do to make it work?
Thanks in advance, and i apologize if this has been answered already but i've looked around in the forums and didn't find any solution.

ps: i dont know if this is useful but this is what i get in console when running java -jar JDownloader.jar:

samba@samba-laptop:~/Documentos/Downloads/jDownloader$ java -jar JDownloader.jar 
19/11/2008 10:00:28 PM - INFO [jd.config.DatabaseConnector(<init>)] -> Loading database
19/11/2008 10:00:28 PM - INFO [jd.utils.JDUtilities(getJDClassLoader)] -> Create Classloader: for: /home/samba/Documentos/Downloads/jDownloader
19/11/2008 10:00:28 PM - FINA [jd.JDClassLoader(<init>)] -> rootDir:/home/samba/Documentos/Downloads/jDownloader
19/11/2008 10:00:28 PM - MÁS FINA [jd.JDClassLoader(<init>)] -> Jar file loaded: /home/samba/Documentos/Downloads/jDownloader/plugins/JDUnrar.jar
19/11/2008 10:00:28 PM - MÁS FINA [jd.JDClassLoader(<init>)] -> Jar file loaded: /home/samba/Documentos/Downloads/jDownloader/restore.jar
19/11/2008 10:00:28 PM - MÁS FINA [jd.JDClassLoader(<init>)] -> Jar file loaded: /home/samba/Documentos/Downloads/jDownloader/JDownloader.jar
19/11/2008 10:00:29 PM - GRAVE [jd.utils.JDLocale(parseLanguageFile)] -> JDLocale: /home/samba/Documentos/Downloads/jDownloader/jd/languages/Spanish.lng.missing not found
19/11/2008 10:00:29 PM - INFO [jd.utils.JDLocale(getLocaleString)] -> Key not found: gui.javacheck.html
19/11/2008 10:00:29 PM - INFO [jd.utils.JDLocale(getLocaleString)] -> Key not found: gui.javacheck.title

---

### Post by taurus on 2008-11-19
What if you install Sun's version instead?

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
sudo update-alternatives --config java
java -version
```

---

### Post by sambita on 2008-11-19
That worked perfectly, i already had those packages installed but hadn't done the --config java part.

Thank you very much for answering so soon :)

---

