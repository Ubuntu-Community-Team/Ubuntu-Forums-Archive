---
title: "Can't Update"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by Wydo on 2009-08-24
[FONT=Batang][SIZE=3]Hi, I had some trouble installing so I downloaded a new ISO file and burned to a boot disk. I finally took a small hard drive and set it up to be my only drive for the install and it went OK and I could boot from it.[/SIZE][/FONT]
[FONT=Batang][SIZE=3]After booting up I find I cannot run update manager and I get this error.[/SIZE][/FONT]
 
[FONT=Batang][SIZE=3]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. [/SIZE][/FONT]
 
[FONT=Batang][SIZE=3]E: _cache->open() failed, please report.[/SIZE][/FONT]
 
[FONT=Batang][SIZE=3]I don’t know anything about linux so any help would be appriciated.[/SIZE][/FONT]
 
[FONT=Batang][SIZE=3]I also need a driver for my onboard sound witch is Realtek 7.1 on my Abit AB9 Pro motherboard.[/SIZE][/FONT]
 
[FONT=Batang][SIZE=3]Thank you[/SIZE][/FONT]

---

### Post by Partyboi2 on 2009-08-24
Hi, do what is recommended, open a terminal (Applications>Accessories>Terminal) and type
```
sudo dpkg --configure -a
```
Hopefully this will fix the problem, if not post the output to the above command.

---

### Post by philcamlin on 2009-08-24
> **Partyboi2 said:**
> Hi, open a terminal (Applications>Accessoires>Terminal) and type
```
sudo dpkg --configure -a
```

+1 that will correct the install error

---

### Post by raymondh on 2009-08-24
> **Wydo said:**
> [FONT=Batang][SIZE=3]Hi, I had some trouble installing so I downloaded a new ISO file and burned to a boot disk. I finally took a small hard drive and set it up to be my only drive for the install and it went OK and I could boot from it.[/SIZE][/FONT]
[FONT=Batang][SIZE=3]After booting up I find I cannot run update manager and I get this error.[/SIZE][/FONT]
 
[FONT=Batang][SIZE=3]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. [/SIZE][/FONT]
 
[FONT=Batang][SIZE=3]E: _cache->open() failed, please report.[/SIZE][/FONT]
 
[FONT=Batang][SIZE=3]I don’t know anything about linux so any help would be appriciated.[/SIZE][/FONT]
 
[FONT=Batang][SIZE=3]I also need a driver for my onboard sound witch is Realtek 7.1 on my Abit AB9 Pro motherboard.[/SIZE][/FONT]
 
[FONT=Batang][SIZE=3]Thank you[/SIZE][/FONT]

As the error message says ... dpkg was interrupted.  Open a terminal (applications > accessories) and type (or copy and paste the command) :

```
sudo dpkg --configure -a
```

You will be prompted for your password which, when you type, will be invisible.

Let's go from there.  Post back if you encounter more errors.

---

### Post by Wydo on 2009-08-24
Hi,
On boot up I notice that if you hit Esc button just before Ubuntu loads you go into a menu that allows you to do a repair.  I did that and it booted with it working and all the updates and I can now add software now too. Yeah! 

Still no sound yet.  Don't know what realtek chip I have because of the heat sinks on the motherboard.

My keyboard and mouse freeze at times too.

thanks

---

