---
title: "Adobe Flash Player in Flock"
date: 2008-10-05
forum: General Help
---

### Post by Prominence on 2008-10-05
How do I install it? Whenever it tries to install it itself it doesn't work, and I don't know any other way.

---

### Post by Prominence on 2008-10-07
Help?

---

### Post by Gondee on 2008-10-07
Put this code in the terminal
```
sudo apt-get install flashplugin-nonfree
```

If it dosn't work, be specific on what it said

---

### Post by Prominence on 2008-10-08
I cna't play YouTube videos in Flock, or anything else that uses the flash player or whatever it is.

---

### Post by QwertyManiac on 2008-11-30
To enable Flash in Flock 2.0.2:

```
sudo ln /usr/lib/flashplugin-nonfree/libflashplayer.so /usr/share/flock/plugins/libflashplayer.so
```

Then restart your Flock browser to get it into effect :)

---

### Post by cupevampe on 2008-12-01
> **QwertyManiac said:**
> To enable Flash in Flock 2.0.2:

```
sudo ln /usr/lib/flashplugin-nonfree/libflashplayer.so /usr/share/flock/plugins/libflashplayer.so
```

Then restart your Flock browser to get it into effect :)

wow thanks man!

---

### Post by raseel on 2009-08-16
> **QwertyManiac said:**
> To enable Flash in Flock 2.0.2:

```
sudo ln /usr/lib/flashplugin-nonfree/libflashplayer.so /usr/share/flock/plugins/libflashplayer.so
```

Then restart your Flock browser to get it into effect :)

Thanks a lot. This helped immediately.

---

### Post by maddog69 on 2009-08-16
> **QwertyManiac said:**
> To enable Flash in Flock 2.0.2:

```
sudo ln /usr/lib/flashplugin-nonfree/libflashplayer.so /usr/share/flock/plugins/libflashplayer.so
```Then restart your Flock browser to get it into effect :)
can u help me out haveing problem with my flash player and i cant upgrade enything every time i do i get this : dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. all i want is my flash player to work been at it for 2 weeks and still not working](*,)

---

### Post by cristalshield on 2009-08-21
hi im having the same problem, but im using flock 2.5.2 and i already got flash player 10 install, i have try all you have list here and this is what i got:

[COLOR=Red][B]sudo ln /usr/lib/flashplugin-nonfree/libflashplayer.so /usr/share/flock/plugins/libflashplayer.so
ln: accediendo a «/usr/lib/flashplugin-nonfree/libflashplayer.so»: file does not exits or directory[/B]
[/COLOR]:KS

---

### Post by cristalshield on 2009-08-21
help

---

### Post by Karloman on 2009-08-27
flash is now installed in another directory, try:

```
sudo ln /usr/lib/adobe-flashplugin/libflashplayer.so /usr/share/flock/plugins/libflashplayer.so
```

This worked for me.

---

### Post by smart ali on 2009-08-31
i'm using Flock 2.5.2 

i have installed the copy from flash player website, it didn't work for me.

i have got this message when i used youtube 
[IMG]http://farm4.static.flickr.com/3509/3875641298_cdf0a57e67.jpg[/IMG]

Do you have any idea for that?

---

### Post by smart ali on 2009-09-01
guys do you have any idea of doing it?

---

### Post by kliner_esprit on 2009-09-15
I've had the same issue and the code posted by Karloman solved the problem.

---

### Post by frevh on 2009-10-02
same as cristalschield  ! an someone help us ?

---

### Post by mmaurycy on 2010-01-06
in ubuntu 9.10 
sudo ln /usr/lib/flashplugin-installer/libflashplayer.so /usr/share/flock/plugins/libflashplayer.so

---

### Post by sonofzell on 2010-04-20
mmaurycy is right on the money, but perhaps I could help translate for some newer Ubuntu users like myself.

Quoted from an [excellent new Linux user blog]("http://helpforlinux.blogspot.com/2008/12/get-flash-working-in-flock-browser-in.html"):

[FONT=verdana]Fire up the terminal and paste this in it:[/FONT]
[FONT=trebuchet ms]**sudo nautilus**[/FONT]

[FONT=Verdana]Navigate to the folder:[/FONT]
[FONT=Verdana]**[FONT=&quot]usr/lib/firefox/plugins[/FONT]** and copy the only file present there 'flashplugin-alternative.so' [/FONT]
[FONT=Verdana]to this folder:[/FONT]
[FONT=&quot]**/usr/share/flock/plugins/**[/FONT]
[FONT=Verdana]Restart Flock and you will have flash working.[/FONT]

Worked like a charm on two Ubuntu 9.10 systems.

Cheers!
-K

---

