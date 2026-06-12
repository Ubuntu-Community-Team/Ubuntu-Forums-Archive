---
title: "Ftp"
date: 2009-06-27
forum: Installation &amp; Upgrades
---

### Post by jet-san on 2009-06-27
Hello,

I'm kinda new with Ubuntu, so forgive me nooby question please:)

I've been looking for nice ftp server program.
I have no idea which one is good or not.
At the moment I have "Filezilla", but friend told me "vsftpd" is better.
Now I can't uninstall "Filezilla"!:(
I tried: Applications => Add/Remove... and it's NOT ticked there, like it would NOT be installed.
Later I tried apt-get (E: Invalid operation uninstall) and aptitude uninstall (This aptitude does not have Super Cow Powers.), but it doesn't work as well.:/

How can I remove it?
Still have it in Applications => Internet.

Is "vsftpd" a fine program?
I need ftp only for send sometimes some files from my brother's pc downstairs.

Regards
Jet

---

### Post by NiN on 2009-06-27
Could you please clarify, what you want?

As far as I could get from the filezilla homepage, it is a FTP client program (for that  you can use the included filebrowser, just hit <ctrl? + L and type the URL in).

If you need an ftp server, vsftp is a good choice, but you will have to read it's manual and understand the configuration, becaust the setup is configuration file only to my knowledge.

---

### Post by jet-san on 2009-06-27
What do I want?
heh:)
First of all I want to remove Filezilla=]

What do I need?
Easy-use FTP...
I want to share my files, so I need a ftp server, right?
On Windows XP I use Cerberus FTP - I run it on my pc and can go downstairs to my brother's computer ans send/download files from my pc.

I need same thing for Ubuntu!:D

Regards
Jet

---

### Post by NiN on 2009-06-27
Well, don't know how you installed filezilla, so I can't help you with that.

Regarding filesharing, why not use samba windows filesharing?

You can share folders using right click in nautilus (file-browser) that way.

As for using FTP, I don't know an easy solution for that (Haven't used it that way in a couple of years)

---

### Post by jet-san on 2009-06-27
Oh, yes, I got it!!!

I've removed Filezilla by Synaptic Package Manager and that's probably the way I've installed it:P
Anyway done!:D

So u recommend sharing folders in Nautilus.
Didn't know about this option-.-
How can I connect in this situation from my brother's pc (Win XP)?
It's probably not same as with ftp by typing in file browser [ftp://168](ftp://168)...

P.S.
What means these "Ubuntu signs" next to some applications in Synaptic?
Are they official software or something?

&

Everytime I shut down my Ubuntu I can hear a "beep" from PC speaker(?).
Can I turn it off?

---

### Post by NiN on 2009-06-29
Well, since it's windows filesharing, you connect to your computer by typing in \\computername in windows explorer (or browse the network places, it should be listed there)
From another linux machine (assuming it is ubuntu or another gnome desktop) just hit ctrl + L  and type ins smb://computername to connect.

The ubuntu signs mean that the package is officially supported by canonical (so it is a package from main)

Regarding the sound issue, I don't know where to turn that off.

---

### Post by jet-san on 2009-06-29
Thanks a lot m8!:)

---

### Post by jet-san on 2009-08-05
It's me again.

I want to change my Ubuntu 32bit to 64bit version, so I wanted to transfer some files.
I've created new folder "Lifeboat" in "Documents" and went to "Sharing Options".
I've ticked all 3 boxes ("Share this folder", "Allow other...", "Guest access".
Then I tried to get in there from my brother's PC (Win XP).
I've typed "\\168.xxx.x.xx" and pressed "Enter".
IE told it can't find such a file...
It's actually a directory not a file, so what should I do now?
I've tried "\\168.xxx.x.xx/Lifeboat" - doesn't work as well.

Regards
Jet

---

