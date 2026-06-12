---
title: "intel wifi/wimax 6250 supported?"
date: 2010-03-07
forum: Hardware
---

### Post by svyatoy.ioan on 2010-03-07
hi all

i have sony vaio vpc-s notebook with intel wifi/wimax 6250 card integrated in. Ubuntu detects card but when i trying to up interface, driver faults with error - firmware file iwlwifi-6050-4.ucode not found.

Who knows when support for this card will be available in ubuntu ? Thanks

---

### Post by sophist on 2010-05-24
I have the same issue with my Lenovo Thinkpad t410s.

while i was checking the name wireless device on windows it's shows -Intel® Centrino® Advanced-N + WiMAX 6250

but in

Ubuntu it shows 

Intel WiMAX/WiFi Link 6050 series

I found at Intel website for Linux they are supporting

Intel® Centrino® Advanced-N + WiMAX 6250  for Linux


[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=17045&ProdId=3199&lang=eng]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=17045&ProdId=3199&lang=eng")


i'm really confused

---

### Post by BennBuntu on 2010-05-29
Intel has a strange way of 'supporting' this card. It's recognised by the kernel module but the microcode that makes the card work hasn't been released yet. They say sometime in third quarter.
 [http://intellinuxwireless.org/?n=Info]("http://intellinuxwireless.org/?n=Info")

Bit dissapointing, but seems we'll just have to wait a few months.

---

### Post by BennBuntu on 2010-06-03
Woot!, been checking daily, ucode released, seems to work ok. Wifi only, no Wimax. Many thanks to Intel.

[http://www.intellinuxwireless.org/?n=Downloads]("http://www.intellinuxwireless.org/?n=Downloads")

---

### Post by usctrojan on 2010-06-12
Hi BennBuntu

Can you please tell me the steps you took to get the 6050 microcode working for your machine.

Thanks a lot

---

### Post by BennBuntu on 2010-06-12
Hi usctrojan,

I just downloaded iwlwifi-6050-ucode-9.201.4.1.tgz from [http://www.intellinuxwireless.org/?n=Downloads]("http://www.intellinuxwireless.org/?n=Downloads")

Then extracted and copied, /lib/firmware/
```
sudo cp iwlwifi-6050-4.ucode /lib/firmware
```
Then reboot, or reload the kernel module
```
sudo rmmod iwlagn
sudo modprobe iwlagn 
```

It worked ok from there, although perhaps not completely reliable. I was having to unload and reload the kernel module after disconnecting from a network.

 I've since upgrade to 2.6.34 using pre-compiled .deb packages, and it's been solid since then.

---

### Post by Walt Norblad on 2010-07-21
I had a very similar problem. I had just bought a Dell Studio XPS 16 with the Intel wifi/wimax 6250 installed. I tried this suggestion, but it didn't quite work for me. However, it did make me think down a different path. I did a quick apt-cache search for wireless. I found this package that seemed to make sense, but patches the kernel.

```
sudo apt-get install linux-backports-modules-wireless-lucid-generic
```

---

### Post by rugito on 2010-08-09
Hi Walt. I tried installing the package you mentioned, but it still does not work. Did you have to choose the driver you wanted, once the package was installed?

---

### Post by fsm_apostle on 2010-08-11
> **BennBuntu said:**
> Woot!, been checking daily, ucode released, seems to work ok. Wifi only, no Wimax. Many thanks to Intel.

[http://www.intellinuxwireless.org/?n=Downloads]("http://www.intellinuxwireless.org/?n=Downloads")

The WiMAX works. I'm using a 6250 WiMAX card now with a Dell Mini 1012 and Clear in 10.04. I followed the instructions here to get it working:

[http://www.linuxwimax.org/Download?action=AttachFile&do=get&target=wimax-announcement-v1.5-2.txt](http://www.linuxwimax.org/Download?action=AttachFile&do=get&target=wimax-announcement-v1.5-2.txt)

---

### Post by rugito on 2010-08-11
If it might help someone...
 
I solved the problem installing the [FONT=Courier New]linux-backports-modules-wireless-lucid-generic [/FONT][FONT=Verdana]package. Then by using[/FONT]
 
```
sudo modprobe iwlagn
```
 
everything worked. To get the module to be loaded at startup, add the line [FONT=Courier New]iwlagn [/FONT][FONT=Verdana]at the end of the [/FONT][FONT=Courier New]/etc/modules[/FONT][FONT=Verdana] file.[/FONT]
 
Cheers.

---

### Post by version7x on 2010-09-08
> **fsm_apostle said:**
> The WiMAX works. I'm using a 6250 WiMAX card now with a Dell Mini 1012 and Clear in 10.04. I followed the instructions here to get it working:

[http://www.linuxwimax.org/Download?action=AttachFile&do=get&target=wimax-announcement-v1.5-2.txt](http://www.linuxwimax.org/Download?action=AttachFile&do=get&target=wimax-announcement-v1.5-2.txt)

fsm_apostle - i've been hitting a bunch of hurdles trying to get this to compile on ubuntu.  the directions you've linked to seem to have a couple of gaps for non-fedora users.  

Do you have any more information on the steps you went through to get this fix into your kernel?

It could be my lack of experience in compiling kernels the ubuntu way, but I'm not sure where to put the git repository.  I get make errors with the locations I've used.  I'm also not sure which packages are required to get it all started.

Thanks!

---

### Post by jbrkeith on 2010-10-01
Hi, I just tried BennBuntu/rugito's suggestions but it's still not working for me...here is what I did:

* downloaded iwlwifi-6050-ucode-9.201.4.1.tgz from [http://www.intellinuxwireless.org/?n=Downloads](http://www.intellinuxwireless.org/?n=Downloads)
* sudo cp iwlwifi-6050-4.ucode /lib/firmware
* installed linux-backports-modules-wireless-lucid-generic
* (optionally) tried adding iwlagn at the end of the /etc/modules file.

and rebooted...no deal...anyone see immediately what i'm doing wrong?

---

### Post by jbrkeith on 2010-10-01
...and to further show my ignorance of ubuntu, i have to confess that after doing all that my wireless is mysteriously disabled in network-manager and i can't seem to reenable it, even my uninstalling the backports...

---

### Post by ericwwheeler on 2010-10-22
> **fsm_apostle said:**
> The WiMAX works. I'm using a 6250 WiMAX card now with a Dell Mini 1012 and Clear in 10.04. I followed the instructions here to get it working:

[http://www.linuxwimax.org/Download?action=AttachFile&do=get&target=wimax-announcement-v1.5-2.txt](http://www.linuxwimax.org/Download?action=AttachFile&do=get&target=wimax-announcement-v1.5-2.txt)

Hey fsm_apostle I just purchased the same machine from Clear. Could you do a quick write up for getting the wimax up in Ubuntu?  I have followed the thread to get the wifi up and could use some help with the wimax instructions.  thanks in advance
Eric Wheeler

---

### Post by fanism on 2010-11-12
> **BennBuntu said:**
> Hi usctrojan,

I just downloaded iwlwifi-6050-ucode-9.201.4.1.tgz from [http://www.intellinuxwireless.org/?n=Downloads](http://www.intellinuxwireless.org/?n=Downloads)

Then extracted and copied, /lib/firmware/
```
sudo cp iwlwifi-6050-4.ucode /lib/firmware
```Then reboot, or reload the kernel module
```
sudo rmmod iwlagn
sudo modprobe iwlagn 
```It worked ok from there, although perhaps not completely reliable. I was having to unload and reload the kernel module after disconnecting from a network.

 I've since upgrade to 2.6.34 using pre-compiled .deb packages, and it's been solid since then.

THANKS SO MUCH, [BennBuntu]("http://ubuntuforums.org/member.php?u=318755").

This works!!!  
I am replying with wireless connection!
btw, mine is Intel 6050 with Linux Mint 9 in a Samsung.  it pointed to the same driver 6050 series

- Vanessa

---

### Post by pythonsyntax on 2011-10-27
Is the  Intel 6250  with wimax it a chip that has 4G and 3G can i use 3G with ths wireless with clear or not?

---

### Post by svyatoy.ioan on 2011-10-27
intel 6250 chip supports wimax + wi-fi (there are two chip modifications - one with 54mbps wi-fi and second with 150mbps wi-fi). other standarts not supported.

---

### Post by pythonsyntax on 2011-10-27
So just has 4G for wimax?

---

### Post by svyatoy.ioan on 2011-10-27
> **pythonsyntax said:**
> So just has 4G for wimax?

what do you mean for 4g ?

---

### Post by pythonsyntax on 2011-10-27
I mean does this wireless and wimax support 3G and 4G wireless with clear?

---

