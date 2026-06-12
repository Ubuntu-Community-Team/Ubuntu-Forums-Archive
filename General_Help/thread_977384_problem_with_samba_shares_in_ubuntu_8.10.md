---
title: "problem with samba shares in ubuntu 8.10"
date: 2008-11-10
forum: General Help
---

### Post by afl on 2008-11-10
Hello !

recently I installed ubuntu 8.10 and now I have major troubles with samba shares that come from a HP3000.

I can mount a share with nautilus, but the directory is empty.
I can even create new files, and they are properly stored on the remote machine...., but after a refresh they are invisible too.

If I use smbclient i can see all files in the remote directory, however i cannot read anything from there ... "permission denied".
Strangely enough I can DELETE files there....

I would really be glad to get some help here, if possible...

For me that looks like a bug, cause it worked in a previous ubuntu-installation and I also have no problems with those shares from NT or XP.

---

### Post by geirha on 2008-11-10
What permissions does the folder on the HP3000 have? It sounds like it has write permissions but not read permissions.

---

### Post by afl on 2008-11-10
As far as I know "write ok = yes" means read and write rights.
I am pretty sure, there is no problem with the server smb.conf, that did not change since ages.
the folder on the server has drwxrwxrwx 
the share as I see it on ubuntu when mounted with smbmount has drwxrwxrwx, the files in there have rwxrwSrwx

---

### Post by aj237769 on 2008-11-10
This has been a problem in 8.10 since i started testing it out 6 weeks ago.  I posted info in a forum that has since been closed and I never received a reply.  The long and short of it from what i can tell is that there is definitely something wrong in Dolphin and Konqueror.  

I have been able to use smbmount to get to my shares but have to issue commands in the terminal manually every time i boot. (I don't want to automate it as the shares aren't always present at boot). 

Contents of my original post (which received one reply on the Kubuntu Forum, simply confirming this issue.)

[http://ubuntuforums.org/showthread.php?t=954733](http://ubuntuforums.org/showthread.php?t=954733) 

(can an admin move this into an open forum since it is not resolved?)

=============================================================================

samba problems in Dolphin and Konqueror
After installing the latest package updates to Kubuntu 8.10 (II), I can no longer connect to any smb file shares on my LAN from Dolphin or Konqueror. I know they are still configured correctly as I can boot any machine to Windows and connect, read, write...just about anything I want to do. I'll also note that one of my machines hadn't been upgraded in about a week and before I went through the adept upgrades today, that machine seemed to be working.

Using smbclient -L <hostname> appears to give the correct results, subsequently connecting via a terminal using smbclient ALSO seems to work.

Dolphin > Network > Samba Shares >
I can see icons for the high-level shares but clicking one results in "File or Folder smb://<hostname> does not exist."

Konqueror > Entering 'smb://<hostname>' results in same error.

I've attached the smb.conf file from the samba server I have set up one one of my machines. The overall architecture I have is as follows:

Sony Vaio - Kubuntu 8.10 (II) - Windows Vista - Samba Server Active
Dell DIM4600 - Kubuntu 8.10 (II) - Windows XP
Russound SMS3 Mediaserver (linux based but not sure abt details)

Has anyone else run into this after the latest round of upgrades? If so any/all suggestions are appreciated.

--I just finished installing today's updates and rebooted, still no luck. I'm attaching the results of smbtree too, not sure if there is something i'm missing. Windows can still see and use all shares.

--Could this be an issue with kio_smb as opposed to samba server or smbclient?

---

### Post by afl on 2008-11-10
It looks as if the filenames, smbclient returns, are missing the last character.
This might be the underlying reason for all samba-shares failing.
I hope that will be fixed soon. Samba not working anymore seems a major bug to me.

---

### Post by ReddogOne on 2008-11-10
Similar problem here. Since I updated can't anything on my Buffalo Terrastation.

Haven't really looked into it but worked 'perfectly' before.

---

### Post by ExCrusader on 2009-02-11
Hi guys, sorry to resurrect a thread that is several months old, but I have been experiencing the same problem in Kubuntu 8.10, and have some information. For some reason when I use: ```
smbclient -L <smb-server-hostname>
``` it returns an ip address that is not on my network, and is most definitely not the ip of that computer. I have no idea why my laptop is doing that, but my xbox running Xbmc works fine. The way around it is to connect using the actual ip address of the server, for example: ```
smb://192.168.0.X
``` in Konqueror. Hope that helps someone else with the same problem.

---

### Post by Emorroiman on 2009-08-25
> **ExCrusader said:**
> Hi guys, sorry to resurrect a thread that is several months old, but I have been experiencing the same problem in Kubuntu 8.10, and have some information. For some reason when I use: ```
smbclient -L <smb-server-hostname>
``` it returns an ip address that is not on my network, and is most definitely not the ip of that computer. I have no idea why my laptop is doing that, but my xbox running Xbmc works fine. The way around it is to connect using the actual ip address of the server, for example: ```
smb://192.168.0.X
``` in Konqueror. Hope that helps someone else with the same problem.
Thanks, Excrusader! Your workaround helped me a lot.

---

