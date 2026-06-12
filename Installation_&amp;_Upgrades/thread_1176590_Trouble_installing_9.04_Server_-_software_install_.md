---
title: "Trouble installing 9.04 Server - software install fails, grub install fails"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by fatherted on 2009-06-02
All right, this has been my inaugural attempt to install Ubuntu Server, and it's not going terribly well for me. 

On the "setup and install software" step, no matter which options I select (auto-install security updates or not, install additional packages or not), it goes through the motions of retrieving the needed files and then goes to a red screen "Installation step failed" with no other useful information. 

I figured since the base system is already installed I could come back and install the software myself later, so skipped to Grub install. I tried Grub2 and that fails with the same type of error. 

I let it install the old Grub, and that seems to have gone fine, but it's irritating that I can't have it go ahead and install LAMP etc. during the setup process. 

I have: 

Verified MD5 of the downloaded .iso
Burned at the lowest speed I can
Verified the burned disc using the utility on the disc (it passed)
Run MemTest86 for 12 hours with no errors
Run the entire system through ultrapro, two passes, with no failures. 
I did dd if=/dev/zero of=/dev/sda bs=1M to nuke the drive and ensure nothing was on it that might be messing with the install, and verified the drive's health with smartmontools. 
All hardware is running at appropriate temperatures. 

So, if the hardware is good, and the .iso is good, and the cd is good, then why is the install failing?

---

### Post by cariboo on 2009-06-02
Do you have a working network connection? It sounds like you are trying to install packages that are in the repositories, which without a working network connection will fail.

---

### Post by fatherted on 2009-06-02
Yes, I do have a functioning network connection - verified by going to 2nd virtual terminal during the install and pinging Google (successfully). 

Side note: I had to physically plug the machine into the router instead of using wireless, as the install script only supports WEP, not WPA - unless there's a config option somewhere that I didn't see. Seems like this ought to be updated sooner rather than later, no? 

At any rate, I tried the install twice, once without configuring the network at all (and presumably forcing it to look only on the CD) and once with eth0 configured. Both had the same error. 

I did notice that sources.list only pointed to the CD until I manually edited it... 

Perhaps I could add the repos to sources.list from the virtual terminal, and THEN try the "install additional software" step? 

Unfortunately I don't have physical access to the machine at the moment, so that bright idea will have to wait until this evening. 

Any ideas about why grub2 didn't like me?

---

### Post by fatherted on 2009-06-03
Finally got a chance to fiddle with this. 

The problem is indeed the sources.list file included on the install CD. 

Not sure if this is by design or what, but the solution was: 

After the base system is installed, when you arrive at the "install additional software" step, alt-f2 to 2nd virtual terminal, edit /etc/apt/sources.list (you'll have to apt-get install your favorite editor to do this) and add the current repository lines for your distribution to it - the default sources.list only includes references to the install cd. 

In my case, that meant adding: 


```
deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted

deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
```then saving the file, returning to the first terminal (alt-f1) and running
the "install additional software" step. There were several additional 
options presented this time - kubuntu and gnome desktops, edubuntu stuff, 
etc., and the install appears to be working fine now (it's downloading a 
lot of packages on my slow connection at the moment, so I'm not 
*completely* convinced it won't error out at the end of the download, but
 I'm fairly confident). 

Hopefully this helps someone else.

---

### Post by fatherted on 2009-06-03
Eh. It seems I spoke too soon. 

Select and Install Software still failed after downloading everything, same error. 

As well, the "configure the package manager" step now has a lot of additional steps which it did not have prior to me altering the sources.list file - it asks whether I want to use a network mirror, what protocol to use for the mirror (http or ftp), and whether I want to use restricted/universe/multiverse/backported/canonical partner packages. 

NONE of these questions were asked before I manually edited sources.list. 

And, no matter how I answer any of the above questions, I now get the "Installation step failed" error on the configure package manager step!

Why does this install script seem to behave so inconsistently? I would think the disc was corrupt or something but I've verified it six ways from Sunday. 

I'm becoming increasingly inclined to just go back to the normal AMD64 Desktop install CD and uninstall what I don't need, distasteful as giving up seems.

---

### Post by fatherted on 2009-06-04
Bump? 

I'd really appreciate some help getting this sorted out.

---

### Post by fatherted on 2009-06-05
Meh. 

I managed to get it sorted myself. (crosses fingers). 

It appears that the problem was a defective BIOS chip. While I was fiddling with this problem the machine actually quit POSTing intermittently. I only managed to bring it back to life by removing the CMOS battery for a long period of time and unplugging the PSU from the motherboard. 

Even after flashing the BIOS, the problem would intermittently recur - fortunately, this board has dual BIOS chips. So, I told it to POST from the backup BIOS and everything has been shiny since, including the full Ubuntu Server install, Grub install, etc. 

Now if I could just figure out how to operate wpa-supplicant from the command line without feeling like a mental deficient...

---

### Post by ric0689 on 2009-10-03
I am having the very same problem you are having/had. I tried installing the Server edition 3 times, all times failed with the same error message. I installed the desktop version and came to find out that tasksel didn't work there either. Have you or anyone found any solution to this problem?

---

### Post by fatherted on 2009-10-03
To be honest, Ubuntu server was so cranky to install, and then so unstable once it was working, and I had such difficulty getting any questions I had answered, that I just installed CentOS 5.3 and have not looked back. Install was a breeze, everything worked right off the bat (other than wifi, which I'd already given up on in Ubuntu Server anyway), and the system's been running 24/7 since June without a single problem. 

If you're really looking for a server OS... I'd recommend going that route. At the datacenter I worked at they ran everything on CentOS 5.2, same deal at my current job (which helps me administer my home server since it's familiar territory).

---

### Post by mutineer612 on 2009-10-12
I had similar problems.  I continued with the installation, rebooted, confirmed network connectivity and then manually added the repositories to the ```
/etc/apt/sources.list
```

Add the following respositories, or edit this list as needed.    
```

deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb http://archive.canonical.com/ubuntu jaunty partner
deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-proposed restricted main multiverse universe
```

Then update the package list with ```
apt-get update
``` and you should be good to go.

---

