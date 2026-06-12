---
title: "Dedicated Server with Ubuntu Desktop installed"
date: 2008-07-24
forum: General Help
---

### Post by SNAPE15 on 2008-07-24
hope this is posted in right section.


Hi, hoping someone can assist with an issue i have. I've been using Ubuntu Desktop on a 2nd pc at home for last few months. Recently i've order a dedicated server from a company who i asked to install Ubuntu Desktop to the server. Now i received the email with ip/masknet/gateway and root passwd. i logged into the server with putty and winSCP and saw that Ubuntu Deskop was installed, well it looked like it as there was a /home/user and under that is the .gconf/desktop/gnome folder but doesnt appear to have the remote access_folder, plus in root folder there is the same .gconf/desktop/gnome folder but with the remote_access folder there and its %gconf.xml file. i checked what version was installed, 
root@servername:~# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.1
Release:        8.04
Codename:       hardy

then also tried to do apt-get install ubuntu-desktop to test, and it said it was already installed, as it should be.


when i emailed the company asking why i couldnt connect to Remote Desktop they said they could...... hmmmm

i then emailed again saying how?
to which i got the reply....

"All of our linux server has the console version installed. We doesn't install the GUI. 

We using putty for connecting to the server."

now i'm really confused......
i'm now waiting on another email reply as to whats going on, is a remote desktop connection setup or what?????

is there a way i can edit some files via putty/winSCP to start up the remote desktop connection and login via vnc, and enable auto login for the user or root???

any help is appreciated. thnx

---

### Post by Execute_Method on 2008-07-24
Is this what you're looking for?

[http://ubuntuforums.org/showthread.php?t=795036](http://ubuntuforums.org/showthread.php?t=795036)

---

### Post by SNAPE15 on 2008-07-24
had no luck with that..... it looks like its about to connect, then says connection terminated?

---

### Post by cariboo on 2008-07-25
Your server is probably sitting at the login prompt. If you have X forwarding setup you can run graphical programs in your terminal. The other thing to do instead of running the desktop on you server is to install webmin. Webmin is a web based server administration suite. You will probably have way better luck using webmin then to try and administer your server from the desktop. There really aren't any programs on the desktop to properly admin your server. Have a look here for webmin:

[http://www.webmin.com/](http://www.webmin.com/)

There is a howto here:

[http://ubuntuforums.org/showthread.php?t=7507](http://ubuntuforums.org/showthread.php?t=7507)

Jim

---

### Post by zipperback on 2008-07-25
[I]> **SNAPE15 said:**
> 
"All of our linux server has the console version installed. We doesn't install the GUI. We using putty for connecting to the server."

now i'm really confused......[/I]



It is a waste of resources to install a gui desktop on a server.

Connect to the server via SSH and administer it that way.
There isn't anything that you need to do on a server that would require you to have a gui desktop.

- zipperback
:popcorn:

---

### Post by SNAPE15 on 2008-07-25
> **zipperback said:**
> **



It is a waste of resources to install a gui desktop on a server.

Connect to the server via SSH and administer it that way.
There isn't anything that you need to do on a server that would require you to have a gui desktop.

- zipperback
:popcorn:


well was only way i knew of being able to run utorrent or something similair

---

### Post by SNAPE15 on 2008-07-25
> **cariboo907 said:**
> Your server is probably sitting at the login prompt. If you have X forwarding setup you can run graphical programs in your terminal. The other thing to do instead of running the desktop on you server is to install webmin. Webmin is a web based server administration suite. You will probably have way better luck using webmin then to try and administer your server from the desktop. There really aren't any programs on the desktop to properly admin your server. Have a look here for webmin:

[http://www.webmin.com/](http://www.webmin.com/)

There is a howto here:

[http://ubuntuforums.org/showthread.php?t=7507](http://ubuntuforums.org/showthread.php?t=7507)

Jim



thnx, i installed this and connected fine. am i able to run a torrent type program with webmin?

---

