---
title: "accessing a xp hd in a remote location"
date: 2005-11-11
forum: General Help
---

### Post by yhotg on 2005-11-11
hi!
first sorry if i am posting to the wrong forum.

now:
i need to access with all the permission the hard drives of my mother's computer throught internet.
her computer runs xp 
and i need to read all the hd and to copy files from her computer to mine
and , if i got there, i would like to listeng to the music in there.

i'm running breezy and kde 3.5beta2

any idea? (i looked on g4l and justlinux but my problem is i don't know what i am looking for. )
thanks

---

### Post by audax321 on 2005-11-11
I would setup an FTP server on your mom's computer to get read/write access to the files. A free FTP server is:

[INDENT][http://filezilla.sourceforge.net/](http://filezilla.sourceforge.net/)[/INDENT]

and there are two that you would have to buy:

[INDENT][http://www.bpftpserver.com/](http://www.bpftpserver.com/)[/INDENT]
[INDENT][http://www.serv-u.com/](http://www.serv-u.com/)[/INDENT]

And for the MP3s, look into this: 

[INDENT][http://www.gnu.org/software/gnump3d/](http://www.gnu.org/software/gnump3d/)[/INDENT]

It can run as a service on Windows and provides a web interface to both stream and download music and video files.

---

### Post by yhotg on 2005-11-11
but maybe i didn't explain myself well enough

i can't setup any server.
i just need to get into my mother computer's hd with full access.
i don't have phisycal access to it, i live on the other side of the ocean and she doesn't know nothing of computers
i just could give her a list of step by step instructions to follow , maybe.
like: go to the start button on the right corner of the screen and there click on control panel (etc etc etc)
u get my meaning?

---

### Post by audax321 on 2005-11-11
Well, to have full access to files you have to setup some sort of server, Windows has some bad security, but its not that bad ;) 

If an FTP server isn't a good solution for you, you could look into a VPN server:

[INDENT][http://www.onecomputerguy.com/networking/xp_vpn_server.htm](http://www.onecomputerguy.com/networking/xp_vpn_server.htm)[/INDENT]

but, I'm not sure how you would connect to it from Linux (never done this before).

Also, if you're worried about having to explain to your mother how to do this, you could setup her computer for remote access and then remotely connect to it using something like rdesktop ([http://www.rdesktop.org/](http://www.rdesktop.org/)) ... might be available in the repos. These are the steps she needs to take to let you connect to her computer:

[INDENT]- START > Control Panel[/INDENT]
[INDENT]- Double-click on System[/INDENT]
[INDENT]- Go to the Remote tab[/INDENT]
[INDENT]- Check Allow Users to Connect Remotely to this Computer[/INDENT]
[INDENT]- Click Apply[/INDENT]

Before you can connect, she must setup a password for her Windows user account. This will give you physical access to her desktop so you could actually set everything up for her by controlling her desktop. But, make sure you have good broadband connections on both ends.

Other than that, I'm out of suggestions. Good luck.

---

### Post by TeraDyne on 2005-11-11
'm trying to do the same thing, though the other computer is on my local network and running Win XP Home. Is it done the same way, or do I have to do something different?

---

### Post by audax321 on 2005-11-11
If you want to share audio/video files using GNUMP3d, you can on your local network.. I do it because of the nice interface.. in that case you access the share using a browser and the address is <local ip>:<port>

For sharing files, from Windows to Ubuntu.. it should work by going through KDE's settings and configuring your workgroup for your windows network.

For sharing files, from Ubuntu to Windows.. you need to setup a samba server. This will let you connect to share folders on Ubuntu using Window's My Network Places. The easiest way to do this is to look at the ubuntuguide... [www.ubuntuguide.org](www.ubuntuguide.org)  You'll have to install the samba (server) package available in the repos.

I feel that samba is crap so I just run an FTP server on my Ubuntu box and access it using a local ip to transfer files. I never have to transfer files to Windows because I don't use it anymore, but if I do then I can just connect to the FTP server and download.

---

### Post by pelle.k on 2005-11-13
Oh man!
This isn't easy, because if it was, you'd already have found a solution.
But it can be done. If your mommy has a firewall in a router protecting her computer this will be "medium" difficult. (IF Its so - let me now about it)
If she has only the built in XP firewall ( I assume SP2 here, because noone should run XP without it.) this will be a "fairly" easy task.

1. Install TightVNC on your computer (xtightvncviewer in synaptic - I think you need universe respitory for this. do you know how that is done?)

2. let her install tightvnc on her computer. the download link is:
[http://www.tightvnc.com/download.html](http://www.tightvnc.com/download.html)
The first file is the windows self-installing package. just tell her to anwer yes to all questions. You know what i mean.

3. this is taken from the documentation. It's not very hard to understand or guide you mom through.

* To make a machine accessible even if there is no user logged in, and to make the server start automatically after reboot, the TightVNC server should be running as a Windows service. To install WinVNC service, choose **Programs->TightVNC->Administration->Install VNC Service**. In Windows 95/98/ME that will start the service immediately, while in Windows NT/2000/XP you'll have to start the service manually using the Services item in the Control Panel (or it will be started automatically on the next system reboot).*

You also have to set a password:
*...to set the default password, you will have to run **Programs->TightVNC->Administration->Show Default Settings.***

4. Ha ha. you asked for it. i told you this will never be an easy task. It doesn't matter who you ask. It's supposed to be hard letting somebody take control over a remote computer!! But anyway, here is the last step:

You have to know her ip-adress. This can be done through entering this address. [http://www.whatismyp.com](http://www.whatismyp.com) in her browser window. The hassle is most ip:s are assigned to a computer dynamicly (means they change - often when one reboots the computer.)
IP adress + a port number (5900 is the port tightVNC uses as default i think):
xxx.xxx.xxx.xxx:5900 would be the port to connect you to her computer using your xtightvnc i think.

NOTICE. This method is completely un-encrypted. Someone might might spy on the data sent between you and the remote computer.
And also - choose a good password longer than five or six characters. You dont want somebody to gain access to you mommys computer do you?

(ADVANCED LEVEL: You could register a dyndns name and install a client on her computer - which would let her computer have a name like memommy.dyndns.org, but as you have no access to her computer (this is a bit much to let your mommy do by instructions... hehe) i'll skip this)

**Maybe you'd be better of with an easy to configure FTP software. Just share the drives you want. I dont know. You be the judge..**

---

### Post by Sloth on 2005-11-13
What you really want to do is to get an SSH server on that machine.  You could then remotely connect to that server and use the FISH protocol to browse the files (built into Konqueror - easy.)    This is as easy as FTP but more secure.  

The easiest way to get that server there is to have her send you a remote assistance request, then install and configure it when you have control of the machine (you may need to use a Windows box to do this, I haven't done it from Linux.)

The major problem is going to be if her machine is behind a NAT router or a firewall, in which case you will probably have to walk her through opening up the ports you need.

---

### Post by yhotg on 2005-11-16
gods! i can't believe is so complex to get into my mother's computer, 

i don't even know what to try first, if the TightVNC or the ftp server or the ssh server,

it looks complicated for me, my mom would get just histerical with the word server

:(

---

