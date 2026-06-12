---
title: "Family Search Indexing not working after update"
date: 2008-08-25
forum: General Help
---

### Post by jdfoote on 2008-08-25
I know there are a few of you out there who use Family Search Indexing (familysearchindexing.org), so hopefully one of you sees this. :)

After the recent update, I haven't been able to get the program to start. Every time I run the iude.jnlp file I get "A special update to the familysearch indexing application has been completed. Start the application as you usually do." and then it removes old JAR files and shuts down.

Is anyone having the same problem, or have you found a workaround?

Thanks!

---

### Post by jdfoote on 2008-08-31
Just in case anyone has the same problem, here is the solution that I found:

The workaround at:
[http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=4729636](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=4729636)

The Indexing application is trying to access the prefs.tmp file with insufficient privileges, so you need to chmod the files it's trying to access.

---

### Post by homargt on 2008-09-13
sorry but i do not speak english

Tengo el mismo error con mi hermano nos paso y no hemos conseguido arreglarlo fui al link

[http://bugs.sun.com/bugdatabase/view...bug_id=4729636](http://bugs.sun.com/bugdatabase/view...bug_id=4729636)

pero no entiendo bien, me gustaria saber que hiciste porque eso del script es solo para solaris?

si pudieras ponerlo paso a paso entenderia lo traduzco con google

[B]
_Traduccion Google_

	
I have the same mistake with my brother we step and we have failed to fix it I went to link

[http://bugs.sun.com/bugdatabase/view...bug_id=4729636](http://bugs.sun.com/bugdatabase/view...bug_id=4729636)

but I do not understand well, I would like to know who did this because the script is only for Solaris?

if you could put it step by step to understand what I translate google[/B]

I have ubuntu 7.04 feisty fawn
I from Guatemala

---

### Post by jdfoote on 2008-09-13
This is the important part of the article:

For the record, these directories need to exist with permissions 755:
/etc/.java/
/etc/.java/.systemPrefs/

These files should be created with permissions 644:
/etc/.java/.systemPrefs/.system.lock
/etc/.java/.systemPrefs/.systemRootModFile

You need to change the permissions for these files. This can be done in the terminal - something like

```

sudo chmod 755 /etc/.java/ /etc/.java/.systemPrefs/
sudo chmod 644 .java/.systemPrefs/.system.lock .java/.systemPrefs/.systemRootModFile 

```



Tiene que modificar los permisos para estos archivos. Puede hacerse en la terminal - algo así como

```

sudo chmod 755 /etc/.java/ /etc/.java/.systemPrefs/
sudo chmod 644 .java/.systemPrefs/.system.lock .java/.systemPrefs/.systemRootModFile 

```

---

### Post by homargt on 2008-09-14
Gracias por contestar amigo, eso que mencionas aqui ya lo había hecho, pero no funciona

 no se si me falta tener algo, mi hermano tiene tambien el java JDK instalado pero tampoco le funcionó
	
Thanks for answering friend, that you mention here had already done so, but it does not work

pentium4-desktop:/etc$ java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

	
I do not know if I do not have something, my brother has also installed the Java JDK but neither worked:(

---

### Post by jdfoote on 2008-09-17
Lo siento. No recuerdo exactamente lo que hice, pero creo que necesitaba cambiar los permisos a todos los archivos a 755 o incluso 666 - Sé que probablemente no es la cosa más segura, sino que trabajó ...

I don't remember exactly what I did, but I think I might have had to change the permissions on all of those files to 755 or even 666 - I know it's probably not the safest thing, but it worked...

---

### Post by firefeather on 2008-09-25
> **jdfoote said:**
> I don't remember exactly what I did, but I think I might have had to change the permissions on all of those files to 755 or even 666 - I know it's probably not the safest thing, but it worked...

I tried changing those permissions to even 666 and it didn't work. I'm also trying to get this same program working for me. Do you have any other ideas what you did?

---

### Post by jdfoote on 2008-09-25
Shoot! I wish I remembered - I want to do all I can to promote FamilySearch :)

And I'm no Linux expert, so chances are I was just guessing when I did whatever I did.

I'm still running FamilySearch, and I can try to tell you my setup.

I'm using Java 1.6.0_06, and both my .java and .systemPreferences look like this when I do an ls:

drwxr-xr-x   3 root root      4096 2008-08-23 11:30 .java

i.e., read and execute permissions for the group and for others. I thought I added write permissions, too, but I guess not.

You could try

```
sudo chmod a+rwx /etc/.java
```

It's probably a bad idea to give that kind of permissions, but I don't know what else to tell you...

---

### Post by firefeather on 2008-09-26
The output of java -version is

```
java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Client VM (build 10.0-b23, mixed mode, sharing)
```I tried the last chmod command even and it didn't help. I just hope someone stumbles across this thread and knows how to help...

---

### Post by firefeather on 2008-09-26
I got it to work! I doubt it's because of the reinstall, but I reinstalled Java so it is the same version as you, and then I followed the instructions I was able to find [here]("https://help.familysearch.org/HelpCenter/main.do?cmd=displayKC&docType=kc&externalId=104566&sliceId=SAL_Public&dialogID=13678841&stateId=0%200%20204055"). I haven't rebooted yet (I wonder if it really will do anything...), but I was able to get in without being stuck in that loop! I will post an update if the fix isn't permanent or totally workable.

UPDATE: Rebooting did allow it to run as a normal user. I didn't expect to find help on the familysearchindexing.org website simply because they said they don't officially support Linux, but it works now!

---

### Post by homargt on 2008-09-27
firefather, I do not speak English but I think it works for you, my question is how to install the older version of Java could put as you did please

	
a little more detailed

    firefather no hablo ingles pero me parece que te funciono, mi pregunta es como instalaste la version anterior de java podrias poner como lo hiciste porfavor

un poco mas detallado

---

### Post by firefeather on 2008-09-30
I don't know how to speak Spanish either, sorry. I don't think the older version of Java is what fixed it. I think it's [what this link says]("https://help.familysearch.org/HelpCenter/main.do?cmd=displayKC&docType=kc&externalId=104566&sliceId=SAL_Public&dialogID=13678841&stateId=0%200%20204055") that fixed it.

> **homargt said:**
> firefather, I do not speak English but I think it works for you, my question is how to install the older version of Java could put as you did please

    
a little more detailed

    firefather no hablo ingles pero me parece que te funciono, mi pregunta es como instalaste la version anterior de java podrias poner como lo hiciste porfavor

un poco mas detallado

---

### Post by mikeazo on 2008-11-14
homargt,

Yo tenia el mismo error que tienes. Haz esto en un terminal:
rm -rf ~/.java/deployment/cache/

I had the same error that you have. Do this in a terminal:
rm -rf ~/.java/deployment/cache/

---

### Post by homargt on 2008-11-15
mikeazo

    Hice eso pero ahora el icono que aparece en el escritorio ya no funciona da un error, ya no encuentra un archivo o algo.

	
I did that but now the icon on the desktop is no longer gives an error, and can not find a file or something

---

### Post by mikeazo on 2008-11-15
Hmmm, no tengo un icono. Intenta empezarlo del sitio [http://www.familysearch.org/eng/indexing/frameset_indexing.asp](http://www.familysearch.org/eng/indexing/frameset_indexing.asp) o trata 'javaws -viewer' en el terminal

Hmm, I don't have an icon. Try starting it from the website [http://www.familysearch.org/eng/indexing/frameset_indexing.asp](http://www.familysearch.org/eng/indexing/frameset_indexing.asp) or try 'javaws -viewer' en the terminal

---

### Post by homargt on 2008-12-10
Sorry but it does not work

---

### Post by homargt on 2008-12-26
Gracias a todos por su ayuda con la nueva actualizacion que hizó Familysearch indexing el 18 de diciembre 2008 el problema se solucionó ya funciona bien.
  Haciendo lo que siempre se hace.

	
Thank you all for your help with the new update did Familysearch indexing the December 18, 2008 the problem was solved and it works well.
   Doing what he always does.:P

---

