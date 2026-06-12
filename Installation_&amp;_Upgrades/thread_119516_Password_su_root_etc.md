---
title: "Password su root etc"
date: 2006-01-19
forum: Installation &amp; Upgrades
---

### Post by robswi on 2006-01-19
When I installed ubuntu a couple of days ago I only remember being asked to establish a password for my user name - which I did and which I have been using with success so far.

I just entered the su command (what does that mean anyway?) to start installing binutils which I apparently need before I can get klik working.  I was asked for a password and my user password didn't work ????

Can anyone point me onward?

Rob

---

### Post by manicka on 2006-01-19
use sudo instead of su

---

### Post by majikstreet on 2006-01-19
sudo whatever... and enter your password for the password.

---

### Post by lha on 2006-01-19
[QUOTE=robswi]When I installed ubuntu a couple of days ago I only remember being asked to establish a password for my user name - which I did and which I have been using with success so far.

I just entered the su command (what does that mean anyway?) to start installing binutils which I apparently need before I can get klik working.  I was asked for a password and my user password didn't work ????

Can anyone point me onward?

Rob[/QUOTE]

Type
```
sudo su
``` and enter your password. su gives you superuser or root shell. As Ubuntu has root account locked by default, there is no password you can enter after su that will be accepted. Instead, Ubuntu uses sudo to do one command as superuser.

---

### Post by Gunnm on 2006-01-19
I'd just like to add (as opposed to starting a whole new thread for a like problem) that I've just installed Ubuntu as well and am totally new to Linux except for Fedora Core, which I used at work, but it was pre-installed, pre-set up and highly regulated (no exploration or tweaks allowed!), and I installed perhaps 4 hours ago. I can't do anything meaningful with it because it continues to ask for my "password" for root. I'm sure many here know the drill... Here's the problems:

- I installed from a downloaded copy that was touted as a "VM" (Virtual Machine). (This is more of a fact than a problem_.

- I was NOT asked to provide an initial password during or after installation

- I was not asked to generate a "new user" at any time, nor am I able to do so.

- I am unable to change settings, add users or install any additional components (like Open Office) without this mysterious "password".

Anyone have any guidance or help on this? This little issue has made my day sad like teardrops...

---

### Post by hatstand on 2006-01-19
Ubuntu setup does ask for a username: it suggests "user" and you type over it if you want. then it asks for a user password. You have to type it in to continue.

there is no other password. your user password is the root password.

If you really didn't get asked to supply a username I think that you took the default, but there is no defualt password: you have to have entered something!

If not, then I'm as stumped as you.

---

### Post by aysiu on 2006-01-19
[QUOTE=Gunnm]
- I installed from a downloaded copy that was touted as a "VM" (Virtual Machine). (This is more of a fact than a problem_.[/quote] I don't know what this means. *Ubuntu* was touted as a virtual machine?

> 
- I was NOT asked to provide an initial password during or after installation This isn't normal. Maybe you should use the regular Ubuntu installer CD instead of this "VM" thing.

> 
- I was not asked to generate a "new user" at any time, nor am I able to do so. Again. Not normal. Get a regular Ubuntu installer CD.

In a *regular* Ubuntu installation, you're prompted to create *one* user and *one* password for that user. That user can temporarily gain root privileges by using the word *sudo* in front of commands. The password is the one you're prompted for during the installation process.

If you weren't prompted to create a user or password during installation, you're not installing Ubuntu. I don't know what you're installing.

Maybe you're using the live CD instead of the installer CD?

---

### Post by Gunnm on 2006-01-19
***Please Note: This problem is now resolved.***

The VM appliance/Ubuntu "flavour" was provided by a company called "VMWare", who offers a browser appliance in conjunction with the core to allow one to surf without worries of spyware/adware/malware. They install a default password for root before sending the core file out for download. Problem was, that I really, REALLY had to dig to get this info to get started.

So now, instead of pulling what's left of my hair out, I'm happilly upgrading the core with apps I need and finally increasing the functionality of Ubuntu past the original intended "safe web browsing". This is a good thing, because this is allowing me to enter the world of Linux OS "risk free" (if something *does* manage to infect the core, it can be simply deleted under Windows and reinstalled. Plus, I've wanted to run a dual OS of Win/Linux for some time, but have been hesitant to do so in the case I managed to bollox things up.

Thanks to all for the responses though, and I guess this is something to keep in the backs of our heads should another confused sould walk through the door. :-D

---

### Post by mainmanc on 2006-01-19
I just installed the VM Ware version also and am having the same issue.  Do you mind sharing what or where you found that information on the root password.

---

### Post by Gunnm on 2006-01-20
[QUOTE=mainmanc]I just installed the VM Ware version also and am having the same issue.  Do you mind sharing what or where you found that information on the root password.[/QUOTE]

No problem... There's a file packaged with the VMWare client called "Getting Started with the VM Browser Appliance", which is located in the system at:

file:///usr/share/vmware-bavm-home/index.html

(copy and paste into your browser nav bar)

You select the "Browser Appliance getting started guide", (which is a .pdf file) link at the bottom, open it with the recommended app, and the two sections of interest are; "Obtaining Root Privileges in the Browser Appliance" and "Changing the User Password in the Browser Appliance".

To save you the hassle though, root access is defaulted to user "vmware" and the password is also "vmware". 'Course, I changed this pretty darned quick ;)

---

### Post by mainmanc on 2006-01-20
Thank you so much.  I am sure this will be very helpful to others.  I am very suprised this isnt covered better, I couldnt find jack squat on the net, and I am not quite sure how the heck you found that info :cool: .

Thanks again for saving me some hair!!

Cheers.

---

### Post by Putztzu on 2006-03-15
Darn,
Just downloaded the VMWare VM, it's a full installation with zilch documentation. Unfortunately, the folder containing the VMWare info is missing in my download. In case it's moved, I'll try to post the name of the file with the info needed, but so far a general search for "vmware" and "appliance" is turning up nothing. Searching on "vm" doesn't turn up anything that's relevant or files which are unreadable.

Only vmware documents I found which are compressed and readable are a changelog (now we know who is uploading images without sufficient documentation!) and a hardware configuration file (no software config file).

Putztzu

---

### Post by Putztzu on 2006-03-15
I can't believe it, as usual after hours of searching and finally posting again I find the answer almost immediately.

You won't find the answer on the machine. See this page for a post and response describing this issue at the VMWare forums

[http://www.vmware.com/community/message.jspa?messageID=338554](http://www.vmware.com/community/message.jspa?messageID=338554)

At the moment, the default root password is "ubuntu" which according to the VMWare forum is the default for any installation of Ubuntu (I wouldn't know that for sure since this is my first install of this distro)

Putztzu

---

### Post by klahjn on 2006-03-15
[QUOTE=Putztzu]I can't believe it, as usual after hours of searching and finally posting again I find the answer almost immediately.You won't find the answer on the machine. See this page for a post and response describing this issue at the VMWare forums [http://www.vmware.com/community/message.jspa?messageID=338554](http://www.vmware.com/community/message.jspa?messageID=338554)
At the moment, the default root password is "ubuntu" which according to the VMWare forum is the default for any installation of Ubuntu (I wouldn't know that for sure since this is my first install of this distro)Putztzu[/QUOTE]

What you might want to do is get one of the Live CD's from the Ubuntu website and if you like it then it has an installer.  It does help alot, because you know from start to finish that a majority of the people on this forum have gone through it at least once, if not several times.  With the VMware version, it seems like something different is done, and you will probably find that some things are alot different from what these forums are used to.  Just a friendly suggestion.

---

### Post by Putztzu on 2006-03-15
Unfortunately, not a solution as I posted in another thread.

The Ubuntu Live CD fails in the middle of the installation unable to recognize the virtual CD if you configure pointing to an ISO file as the CD instead of a real CD.

Anyway, I believe that the VMWare Forum link I posted should answer all questions as well as provide the root password which is "ubuntu"

Putztzu

---

### Post by Putztzu on 2006-03-16
Just another, maybe last addendum...

For anyone who deploys the vmware "appliance" virtual machine, download the regular install ISO for that version also.

Installing additional applications and some configuration modifications will require access to the install CD.

Putztzu

---

