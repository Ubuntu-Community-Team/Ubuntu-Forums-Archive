---
title: "[SOLVED] Java Error! Making me mad!"
date: 2008-08-06
forum: General Help
---

### Post by dddmx3 on 2008-08-06
:confused:Java Error! Making me mad!:confused:



PLEASE HELP!! I NEED THE ANSWER!!

'Javac' is not recognized as an external or internal command, opperable program or batch file.


Please give me a step by step (VERY SIMPLE) tutorial on how to fix this, PLEASE!?!


:(I have the jre1.6.0_02 version.:(

---

### Post by LaRoza on 2008-08-06
[http://ubuntuforums.org/showthread.php?t=713622](http://ubuntuforums.org/showthread.php?t=713622)

---

### Post by plastichero on 2008-08-06
Dont be mad, please :)

Sorry, I'm in a hurry .. just a link for you:

[[COLOR="Blue"]_Visit here_[/COLOR]]("http://shubuntu.blogspot.com/2008/08/installing-java-and-running-simple.html")

---

### Post by tuxxy on 2008-08-06
[http://forums.sun.com/thread.jspa?threadID=445885](http://forums.sun.com/thread.jspa?threadID=445885)

---

### Post by dddmx3 on 2008-08-06
THANK YOU!!!:) For writing back but,:( I'm making a private server and need to find out how to fix that error... Could you guys explain it to me on these forums, not a link. MY BRAIN IS ABOUT TO EXPLODE!!!! (:lolflag:) I've been looking for this answer for about 1 week! I need to get my server running! ASAP!!! PLEASE HELP ME!!!!!!  :cry: :cry: :cry: :cry: :cry:

---

### Post by dddmx3 on 2008-08-06
> **dddmx3 said:**
> THANK YOU!!!:) For writing back but,:( I'm making a private server and need to find out how to fix that error... Could you guys explain it to me on these forums, not a link. MY BRAIN IS ABOUT TO EXPLODE!!!! (:lolflag:) I've been looking for this answer for about 1 week! I need to get my server running! ASAP!!! PLEASE HELP ME!!!!!!  :cry: :cry: :cry: :cry: :cry:

[COLOR="Red"]UPDATE:[/COLOR]

I just seacrhed my C:\Program Files\Java\jre1.6.0_02\bin folder and there is no javac.exe or javac file! But, there is a java.exe file. Is there supposed to be a javac.exe or javac file in C:\Program Files\Java\jre1.6.0_02\bin??

PLEASE HELP!!!!!!

---

### Post by tszanon on 2008-08-06
> **dddmx3 said:**
> [COLOR="Red"]UPDATE:[/COLOR]

I just seacrhed my C:\Program Files\Java\jre1.6.0_02\bin folder and there is no javac.exe or javac file! But, there is a java.exe file. Is there supposed to be a javac.exe or javac file in C:\Program Files\Java\jre1.6.0_02\bin??

PLEASE HELP!!!!!!
Hmm...what?
First: what you got there is the Java Runtime Environment (JRE). What you need is the Java Development Kit (JDK).
Second: "C:\Program Files"? That's Windows. I don't remember where java files are kept, but surely that's not the right place.

Edit: and welcome to the forums!

---

### Post by igotnoluck on 2008-08-06
Hi,
you need the JDK for using the javac component.
please install using:

```

apt-get install sun-java6-jdk

```

that should do the trick :)

---

### Post by dddmx3 on 2008-08-06
[COLOR="red"]UPDATE:[/COLOR]

I just installed JDK 6 Update 7!

BUT, I STILL NEED HELP!!!

---

### Post by dddmx3 on 2008-08-06
> **dddmx3 said:**
> [COLOR="red"]UPADTE:[/COLOR]

I just installed JDK 6 Update 7!

BUT, I STILL NEED HELP!!!

Online and offline installations...

---

### Post by igotnoluck on 2008-08-06
what do you need ? if you run the command i
wrote you everything should run.

---

### Post by dddmx3 on 2008-08-06
> **tszanon said:**
> Hmm...what?
First: what you got there is the Java Runtime Environment (JRE). What you need is the Java Development Kit (JDK).
Second: "C:\Program Files"? That's Windows. I don't remember where java files are kept, but surely that's not the right place.

Edit: and welcome to the forums!

"Java files are kept" what do you mean their installed on C:\Program Files\java that's the stock installation place....

---

### Post by igotnoluck on 2008-08-06
do you want to install java on Ubuntu or Windows ?
because the things you write (C:\...) are windows !

---

### Post by dddmx3 on 2008-08-06
Special Thanks to Tszanon! He/she wrote:

 "First: what you got there is the Java Runtime Environment (JRE). What you need is the Java Development Kit (JDK)."

That was my problem! YAY!!

And guys put your envoirment variables in USER VARIBLES not system varibles!!!!

:KS:KS:KS:KS:KS:KS:KS:KS

---

### Post by tszanon on 2008-08-06
You're welcome. Please, mark this thread as Solved using the Thread Tools menu, at the top.

---

