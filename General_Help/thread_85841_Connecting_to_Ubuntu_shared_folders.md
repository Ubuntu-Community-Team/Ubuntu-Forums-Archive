---
title: "Connecting to Ubuntu shared folders"
date: 2005-11-03
forum: General Help
---

### Post by Randy Sparks on 2005-11-03
I can get Ubuntu to "see" my Windows XP machine just fine and access shared folders. 

What I can't do is access shared folders on my Ubuntu machine from my XP box (yes, I clicked to install SMB and not NFS). 

The Ubuntu machine appears in My Network Places under XP (and also my Win98 machine), but when I try to access it I get a username and password prompt. I try my Ubuntu username and password but that doesn't work. They're the only passwords I've ever entered on Ubuntu! I've tried leaving the password field blank but it won't work. 

Any help appreciated. I've read the Ubuntu Guide and the FAQ and their advice doesn't work. I looked under the Users entry on the System menu to see if I need to enable myself to be Samba orientated, but that seems a blind alley.

---

### Post by mlomker on 2005-11-03
Have you looked at [this how-to]("http://ubuntuforums.org/showthread.php?t=76647")?

---

### Post by Randy Sparks on 2005-11-03
That's good advice and there's some interesting reading there. But is there any way of connecting to an Ubuntu shared folder without having to hack config files?

---

### Post by mlomker on 2005-11-03
Sorry, I don't use Gnome.  Config files are the one common thing, regardless of what desktop manager you are using.  That's one reason why most how-to's will be provided that way.

---

### Post by cts on 2005-11-04
To see an ubuntu share from windiws
Forget about passwords, no-one seems to be able to show how...
Go for no passwords like this **/etc/samba/smb.conf**

#===================================
[global]
   workgroup = OURWORKGROUP
   netbios name = ubuntu
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d

   security = share
   username map = /etc/samba/smbusers
   encrypt passwords = no

   passdb backend = tdbsam guest
   obey pam restrictions = yes

   invalid users = root

   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
   socket options = TCP_NODELAY
   domain master = no
[homes]
 comment = Home Directories
 browseable = no
  writable = no
  create mask = 0700
  directory mask = 0700
[ubuntus]
   comment = ubuntu share
   path = /home/ubuntushare
   public = yes
   create mask = 0777
   directory mask = 0777
   writable= yes
   force user = nobody
   force group = nogroup
#===================================


after saving this file
do 

[B]/etc/init.d/samba restart

[/B]
ps to change hostname do [B]3 things
hostname fred
[/B] change ubuntu in **/etc/hosts** to [B]fred
[/B] in System...network... find the hostname field and change ubuntu to fred

if you just do step 1, lots of complaints

---

### Post by Randy Sparks on 2005-11-04
OK, I've done some more research. I'm not sure if this is a bug or not. :confused: 

Here's my solution for connecting to shared folders within Ubuntu 5.10 from Windows machines. It doesn't involve hacking config files:

- open a terminal window
- type the following

[FONT="Courier New"]sudo smbpasswd -e *<your username>*[/FONT]

- the use of sudo means you'll have to type your main password; after this type a new Samba password as prompted

You should then be able to access your Ubuntu share from Windows machines. The command enables the Samba password for your user account and, I presume, adds you to its password file. 

It worked for me and I can now access from WinXP Home (in Win98 it works so long as you login to Win98 with your Ubuntu username). 

This way there's no need to mess around changing workgroups in the smb.conf file or disabling passwords, which is undeniably insecure (particularly if you don't have a hardware firewall). :smile:

Edit: Dont forget that the XP's built in firewall can get in the way of file sharing - you might have to deactivate it.

---

### Post by mlomker on 2005-11-04
> 
[FONT="Courier New"]sudo smbpasswd -e *<your username>*[/FONT]


Hmm.  According to the man pages that would only re-enable a previously disabled account.  The how-to that I had linked you to uses -a, which adds a new user.

---

### Post by Randy Sparks on 2005-11-04
[QUOTE=mlomker]Hmm.  According to the man pages that would only re-enable a previously disabled account.  The how-to that I had linked you to uses -a, which adds a new user.[/QUOTE]

What I described worked fine for me. I haven't disabled any Samba accounts. In fact, until yesterday, I had never used the Samba components of my Ubuntu install. 

Just now I switched to another account on my system and tried to change the Samba password (ie simpy typing smbpasswd on its own). 

I got this error message:

[FONT="Courier New"]machine 127.0.0.1 rejected the (anonymous) password change: Error was: Account disabled.[/FONT]

This is the same error I got initially and is why I chose to enable the account, rather than add it. Could it be that there's a bug here whereby the GUI tools are creating a Samba account but somehow disabling it, or neglecting to enable it?

---

### Post by mlomker on 2005-11-04
Had you previously created the account with -a?  I just did a **sudo smbpasswd -a username** and it created the samba database and added the account.  The database exists in /var/lib/samba.

I just created a test user to try the commands:

```

mlomker@mlomkernote:/etc/X11$ sudo smbpasswd -e testuser
Password:
Failed to find entry for user testuser.
Failed to modify password entry for user testuser
mlomker@mlomkernote:/etc/X11$ sudo smbpasswd -a testuser
New SMB password:
Retype new SMB password:
Added user testuser.
mlomker@mlomkernote:/etc/X11$

```

---

### Post by Randy Sparks on 2005-11-04
> Had you previously created the account with -a?  I just did a **sudo smbpasswd -a username** and it created the samba database and added the account.  The database exists in /var/lib/samba.

No, I hadn't created the account and/or database. But that's not to say that the GNOME tools didn't. As you've said, you don't use GNOME Ubuntu but here's how creating a shared folder works: when you click on  System - Administration - Shared Folders *for the first time*, you get told that you need to install the SMB packages. 

My suggestion is that the GNOME tools and/or the SMB package autoconfiguration is creating my account and the Samba database but not doing it properly. (The best guess is that it's created but not activated.) 

But I must stress that I use standard GNOME Ubuntu and not Kubuntu where I suspect things are handled differently.

---

### Post by thexaspect on 2006-03-09
Anyone know why I wouldn't be able to write to my shared folder when using the above instructions? I can read everything, it loads up fine in XP Pro, but I can't copy anything to the folder, no drag and drop, copy and paste, etc.

---

