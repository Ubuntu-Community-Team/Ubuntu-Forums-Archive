---
title: "Can't Detect My MP3 Player."
date: 2006-01-02
forum: Hardware &amp; Laptops
---

### Post by CarlosinFL on 2006-01-02
I have a Creative Zen Touch MP3 player (20GB) that I want to use with Ubuntu. I tried just connecting it via USB and nothing happens. Linux does not recognize the player not did the player recognize I connected this to Ubuntu.

I am using Gnome 2.12.1 and would like to know how to get my  player working in Linux so I can drag and drop mp3's into the player.

---

### Post by linuxted on 2006-01-02
[QUOTE=Carlwill]I have a Creative Zen Touch MP3 player (20GB) that I want to use with Ubuntu. I tried just connecting it via USB and nothing happens. Linux does not recognize the player not did the player recognize I connected this to Ubuntu.

I am using Gnome 2.12.1 and would like to know how to get my  player working in Linux so I can drag and drop mp3's into the player.[/QUOTE]


I'm having the exact problem with an ipod nano.  This used to work for me... I have a feeling there is a new bug that crept up somewhere.  I've had no luck fixing it yet.  If it is a bug I suspect a small army of people will be working on it.

---

### Post by dosed150 on 2006-01-02
i dont know if you can just drag and drop you need software for it but your in luck ifd you go to add applications then sound and video then add gnomad 2 that should work for the creative for the ipod nano do the same but download gtkpod instead

---

### Post by CarlosinFL on 2006-01-02
I just installed the **gnomad 2** & it still did not find my Zen Touch :(

---

### Post by raublekick on 2006-01-02
it won't just pop up on the desktop. zen's aren't set up like USB drives, so you have to use gnomad2 to send files. 

since you just installed gnomad2, you'll probably have to open it via the command line using sudo. just plug in the zen, then open a terminal and type:
```
sudo gnomad2
```
then enter your password and gnomad2 should open. it will probably scan your zen's files first. 

gnomad2 is a little unpredictable sometimes, at least for me. it often takes many tries to get it to open so i can send files.

---

### Post by CarlosinFL on 2006-01-02
Yes, I fired up the player and then opened the application and get this error:

[IMG]http://img305.imageshack.us/img305/53/screenshoterror1sl.png[/IMG]

---

### Post by raublekick on 2006-01-03
Did you do it in the terminal with sudo?

---

### Post by CarlosinFL on 2006-01-04
No,

I went to the applications icon and started the app via GUI. What do you mean start this in terminal? Should I just go to a terminal window and "sudo" what command?

---

### Post by cbudden on 2006-01-04
I just got my Creative Zen working.  I had trouble doing it but eventually I used gnomad2 and libnjb packages from dapper.  They are here [http://cbudden.sitesled.com/gnomad2.zip](http://cbudden.sitesled.com/gnomad2.zip) , along with 2 config files you need to put in the folder /etc/hotplug/usb/ .  Install the deb's, put those files in the directory then plug in your player and start gnomad2 with alt-f2 and type ```
 gksudo gnomad2 
``` .  If nautilus says about permission denied when copying the files, start up a root nautilus with alt-f2 and gksudo nautilus.

hope this helps.

---

### Post by CarlosinFL on 2006-01-04
How do I installed the deb's?

---

### Post by Lord Illidan on 2006-01-04
sudo dpkg -i <package name> should install the debs. (remove the <> and replace the package name with the one of your choice.

My Creative Zen Micro works perfectly with Gnomad 2 out of the box. Hope you are not doing something wrong.

---

### Post by cbudden on 2006-01-04
[QUOTE=Lord Illidan]sudo dpkg -i <package name> should install the debs. (remove the <> and replace the package name with the one of your choice.

My Creative Zen Micro works perfectly with Gnomad 2 out of the box. Hope you are not doing something wrong.[/QUOTE]


A friend of mine has a Zen Micro, which worked straight off but my Zen didn't.

---

### Post by Mozzer on 2006-01-06
[QUOTE=cbudden]I just got my Creative Zen working.  I had trouble doing it but eventually I used gnomad2 and libnjb packages from dapper.  They are here [http://cbudden.sitesled.com/gnomad2.zip](http://cbudden.sitesled.com/gnomad2.zip) , along with 2 config files you need to put in the folder /etc/hotplug/usb/ .  Install the deb's, put those files in the directory then plug in your player and start gnomad2 with alt-f2 and type ```
 gksudo gnomad2 
``` .  If nautilus says about permission denied when copying the files, start up a root nautilus with alt-f2 and gksudo nautilus.

hope this helps.[/QUOTE]
This so works. Thanks very much, I got a "Zen Nothing" off ebay the other day for just £120, and this means I don't have to use Windows for file transferring shennanigans :D

---

