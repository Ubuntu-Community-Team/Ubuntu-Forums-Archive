---
title: "Flash-making app ?"
date: 2005-11-28
forum: General Help
---

### Post by Bachstelze on 2005-11-28
Can anyone suggest an app to make Flash animations ? WINE can't run Macromedia's Flash MX...

---

### Post by Corvillus on 2005-11-28
You can run Flash MX, but not Flash MX 2004.

---

### Post by Bachstelze on 2005-11-28
[QUOTE=Corvillus]You can run Flash MX, but not Flash MX 2004.[/QUOTE]

Oh, ok, the only version I tried was 2004... I'm gonna check the WINE database to see which versions work. Thanks for the tip :)

---

### Post by crazyness003 on 2005-11-29
What about Flash 8 pro?

---

### Post by kaffelars on 2005-11-29
There's an app called Flash 4 Linux ([http://f4l.sourceforge.net/]("http://f4l.sourceforge.net/")). I haven't tried it however, just installed it.

The deb-package wouldn't install because of a package being the wrong version, but converting the RPM-package to a DEB-package with alien worked for me:

[LIST=1]
[*]Download the RPM-package
[*]If you haven't got it already, install alien by typing **sudo apt-get install alien** in a terminal.
[*]Type **alien -d <NAME_OF_RPM_FILE>** (being in the directory where the downloaded RPM-file is)
[*]You now have a WORKING deb-file that you kan install with **dpkg -i <NAME_OF_DEB_FILE>** in a terminal.
[/LIST]
:o

---

### Post by tomwell on 2005-11-29
Kaffelars,

Hey just installed flash 4 linux, what is the launch i need to type in terminal, it doesnt seem to have created a entry in applications...

Thanks man

Peace

Tom

---

### Post by kaffelars on 2005-11-29
The command for launching is simply **f4l** :) 

Good luck :)

---

### Post by tomwell on 2005-11-29
kaffelars,

It tells me command not found i had tried that one.... lol

when i go in sysnaptics i can see its installed attached screen shot perhaps you will see something i dont...

Thanks for your help....

Tom

---

### Post by kaffelars on 2005-11-29
Hmm, that's odd..I have it working on both of my computers. What i DO see however is that you seem to have a different version (0.2-2) than me (0.2-1). 

Anyway, I uploaded the package i use  [here]("http://home.hia.no/~lebjor02/downloads.php"), just click on **Last ned**.

---

### Post by tomwell on 2005-11-29
Kaffelars,

Thank you, will try using this one...

Keep you posted...

Peace 

Tom

---

### Post by tomwell on 2005-11-29
WORKS!!!! YES!!!!

Thank you so much Kaffelars...!!!

Peace

Tom

---

