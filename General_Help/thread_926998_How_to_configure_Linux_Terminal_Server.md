---
title: "How to configure Linux Terminal Server"
date: 2008-09-22
forum: General Help
---

### Post by koganin on 2008-09-22
Hi all,

I am very new to the Linux computing scene and so I apologize in advance for my noob questions. Any help, however, would be greatly appreciated!!

I just recently configured a server at home with Xubuntu 7.04 (Feisty) and although it took me some time to figure it out and find some help it was definitely a good learning experience. I followed the instructions I found on bit-tech.net.

However, there is a server that I was asked to configure in the lab that I work in. I'm really enthusiastic about learning more about the Linux computing environment so I decided to try and configure it.

The server is a Dell PowerEdge 2900 III. Right now, it has two hard drives (1TB and 250GB), two ethernet cards, and 4GB RAM. In the lab, we use two applications that are relatively memory-intensive. App#1 runs only on Linux and App#2 runs only on Windows.

What I'd like to do is setup this server with two workstations (thin-clients?) that can make use of the server at the same time. However workstation1 should be able to run linux while workstation2 should be able to run windows (or vice versa).
I'm just a bit confused as to how to go about configuring this.:confused:

From what I've read, I can install an LTSP server from the 8.04 ISO. But I'm not too sure about how to configure the network devices and the IPs.
With this configuration, would I be able to accommodate the following scenarios? :
1. Take workstation1 and run App1(runs on Linux only)
2. Take workstation1 and run App2(runs on Win only)
3. Take workstation2 and run App1
4. Take workstation2 and run App2

Again, I apologize for such a long post and these beginner questions. Any help would be very greatly appreciated!! :)

---

### Post by Taxman415a on 2008-09-22
Well the server can only boot into one operating system at a time unless you use virtualization such as Vmware or Virtualbox, etc. But that is possible. To do what you want you could install Ubuntu on the server and install Windows inside of a virtual machine running on Ubuntu. You would need a lot of memory to do that. 

Then the LTSP could handle configuring the thin client workstations. Basically with LTSP you don't have to worry about the IPs and so forth it handles them automatically by default. By far the easiest way for you to do this would be to install Edubuntu instead and read this [http://www.edubuntu.org/GettingStarted](http://www.edubuntu.org/GettingStarted)  
It is set up by default to be a terminal server if you pick the first install option.

Then you would just need a solution to run the Windows apps on the thin client workstations. I've not done that myself, but it could be configured using something such as VNC. Go to System -> Preferences -> Remote Desktop  on the server and you can set that up.

---

### Post by koganin on 2008-09-22
Taxman, thanks for the response and the info!

I noticed that the latest version of Edubuntu has a new installation procedure to go along with the Hardy Heron release:
  1. Install either Ubuntu Desktop CD / Alternate CD
  2. Install Edubuntu Add-Ons CD

The link you provided takes me to the Edubuntu 6.06.1 release. Would you suggest the newer release over 6.06.1? 

Thanks again :)

---

### Post by Taxman415a on 2008-09-22
You probably want the latest version, I was just showing you that for background on what it can do for you and to make it easier to understand. There's also just a package you can install that installs all the Edubuntu functionality, I just don't think it is quite as easy for you as installing Edubuntu from scratch and I don't recall the packagename off the top of my head. It might just be edubuntu-server. You may not need the Edubuntu Add on CD since that just has the extra applications. The primary benefit of Edubuntu for the needs you asked about is the relative ease of setting up the thin clients.

---

### Post by koganin on 2008-09-22
Taxman, no problem. Duly noted. :)

I'll go ahead with the install and keep adding on to the notes I've been taking.

I'll definitely post an update here

---

### Post by koganin on 2008-09-22
I was able to successfully install the LTSP setup from the Ubuntu 8.04.1 Alternate CD onto the server box. I may be missing something here, but I assumed that the next step would be for me to go ahead and right away boot my thin-client (my laptop) thru the PXE protocol.

I tried to boot off the network via PXE protocol but was unable to do so. Error msg is: Unable to locate bootable ROM file (or something along those lines).

Any help would be appreciated guys. Thanks in advance.:)

---

### Post by Taxman415a on 2008-09-22
Yes, as I understand it, if it was set up right that would be the next step. What may be happening is that you have competing DHCP servers on the network, so the thin client isn't getting it's IP address from the LTSP server thus it can't find the boot file. Do you know what is acting as the DHCP server for the network? 

If you don't there are two ways to test the issue. Try unplugging the server from the network and plug the thin clients only directly into the server (i.e. have those be the only things attached to the switch/hub)

The other way is to look at the output of ```
ifconfig -a
``` on both the server and the thin clients. Since the thin clients don't boot with PXE, boot them into Linux (from a Livecd if needed) normally and run that command to see what address they pick up.

As I understand it the Edubuntu livecd actually works as a terminal server, so you can boot into it and test it out without even installing it. If you run into the same issue that's more evidence it's a DHCP conflict issue.

---

