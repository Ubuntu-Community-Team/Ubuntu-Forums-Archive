---
title: "Newbie needs some help ;-)"
date: 2008-09-23
forum: General Help
---

### Post by tangoforce on 2008-09-23
Hi guys!

I've recently installed ubuntu in a VM to try it out. I've copied it across to another networked machine and managed to get the internet etc working on both.

Now I'm having some problems.

I was fully intending to use ubuntu as my full time 24/7 network server for files, http, ftp, printer etc. I've built a box specially for this task.

The problem? Access. I have one KB, monitor, mouse which is connected to my MAIN PC.

Obviously VNC won't allow me to access ubuntu unless someone has already logged onto the box and created a session/desktop to share.

So.. I found this thread: [http://ubuntuforums.org/showthread.php?t=335548](http://ubuntuforums.org/showthread.php?t=335548)
Inspiring stuff right? Yes.. sorta.

It seemed like a brilliant idea. I got it up and running and then had a funny feeling. So.. I left a file on the desktop. Logged off, logged in remotely... No file on the desktop. Went local, file is still there on the desktop. So.. remote access is only creating a virtual session which doesn't give me access to my files on the remote ubuntu box.

So.. to recap:
1) The target physical machine has no keyboard, monitor or mouse and so needs to boot and accept remote logins with no local user logging in
2) I need to access the same desktop each time - not a virtual one that starts clean..
3) VNC won't work because there isn't a user already logged on - It also doesn't allow you to log in with a username - just a password and screen.

What I am looking for is basically something like Windows XP Remote Desktop access but for linux.

Can anyone recommend the way forward please?

Obviously I want to use Linux as I keep hearing how much better than windows it is (despite bad experiences with Suse not supporting PCI 56k modems, wifi, etc). I'm sure it must be possible to duplicate XP's behaviour in ubuntu?!

Many thanks

---

### Post by Bakon Jarser on 2008-09-23
I haven't used it but it looks like FreeNX will do what you want.

You should use more descriptive titles when starting a thread.  You are more likely to get help that way.

---

### Post by tangoforce on 2008-09-23
I thought FreeNX also created virtual sessions?

Thanks for the tip - I should of also posted in the newbie forum too but didn't see it! Whoops..

---

### Post by Bakon Jarser on 2008-09-23
> FreeNX is a system that allows you to access your desktop from another machine over the internet. You can use this to login graphically to your desktop from a remote location

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

### Post by tangoforce on 2008-09-23
> 
For Ubuntu 7.04, they are:

deb [http://mirror.ubuntulinux.nl/](http://mirror.ubuntulinux.nl/) feisty-seveas freenx
deb-src [http://mirror.ubuntulinux.nl/](http://mirror.ubuntulinux.nl/) feisty-seveas freenx

For Ubuntu 8.04 and 8.10 you find the necessary information at [https://launchpad.net/~freenx-team/+archive/](https://launchpad.net/~freenx-team/+archive/). 


I looked at the site, and couldn't see any links in a similar format to those above at all.
I thought linux is superior to Windows? - Why is there a different version for each version of Ubuntu? - Am I going to suffer dependency hell with Ubuntu?

Also, considering I was told Ubuntu is far easier to understand, why am I not able to see the information I want on the same page?

I hope I'm not being stupid, but it just doesn't seem as straight forward as I was lead to beleive. Sure Ubuntu itself so far seems ok - I've got my network up and running etc but I've always found that linux package installations far from straight forward (Suse's YAST was a awful experience - especially trying to install openoffice - again there were about 30 different versions for each version of Suse - why?)

Thanks

---

### Post by tangoforce on 2008-09-23
Is there not an automated way of installing this? Being a Windows man in general, everything is normally double click>check some boxes, click some agree buttons, watch a progress bar, possible restart and done.

I can't remember the last time I had to use the command line to install something. It seems that ubuntu isn't as easy to grips with as I was told! I don't understand... Why is it always command line based with linux?

---

### Post by taladan on 2008-09-23
This may be a little beyond the scope of your question, but is there a reason that you can't use a web-based administration tool for the ubuntu box such as webmin, and then use SSH/SFTP to upload files to it or do other CLI administration tasks that are too roundabout to work with in webmin?  I know that I use webmin on several different ubuntu/kubuntu linux boxes both at home and at work to administer everything from webservers to DNS, DHCP, SAMBA, pretty much anything you can install on a linux box.  This will allow you to remotely administer the machine from anywhere without having to have specialized software installed on the 'client' box you're connecting from.  

Just a thought,

Tal

---

### Post by tangoforce on 2008-09-24
Hi

Well I used to use webmin years ago on a webhosting package I had. Back then I found it rather daunting not being a native linux man so as you can probably imagine I'm trying to avoid it!

Give me a GUI anyday ;)

The problem with linux is that it demands that you use the console for a lot of things which Windows while not being the best of OS's is generally point and click for most tasks. Even now I use the prompt sometimes in windows but all the linux commands are all different. It's like starting to learn a computer again all from scratch in some ways. Obviously I can navigate the desktop and setup my network etc (although in knoppix v3 thats a pig as its prompt based) but I fail to see why installing packages means you have to download and install from the prompt.

Whats wrong with a good old download manager and double clicking to start the setup :confused:

Not only that, I'll never understand why there is a different download for every version of the same OS, every version of the kernel etc. Being a winblows man it all seems very bizzare.

Looks like I'm going to have to stick with XP...

---

### Post by taladan on 2008-09-24
Well, the original question wasn't regarding package management and being able to install things without the command line - that I saw.  If you want to deal with package management, try synaptic or adept or aptitude...one of those will more than likely serve all your needs.  

Regarding the original question though, it was how to run a headless server and I simply thought that a web based interface would be more serviceable than worrying with vnc clients or rdp clients or anything like that on each machine you might want to access the box from.

Tal

---

### Post by Bakon Jarser on 2008-09-24
Most users can get by without ever using the command line.  Most people use command line to offer help because it is easier to tell someone to copy and paste code then to tell them go to this menu then click this tab etc, etc.  If you want a gui for adding and removing programs just click applicatons and click add/remove on the bottom.  You can also go to system > Administration > synaptic package manager.  FreeXN happens to be a program that isn't in the package manager.  The creators have also not created a .deb. .deb files are just like install.exe files in windows.

[http://ubuntuforums.org/showthread.php?t=135036](http://ubuntuforums.org/showthread.php?t=135036)

[http://ubuntuforums.org/showthread.php?t=541656](http://ubuntuforums.org/showthread.php?t=541656)

---

