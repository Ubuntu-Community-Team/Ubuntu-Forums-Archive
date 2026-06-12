---
title: "Network PXE install problem - n00b"
date: 2009-03-30
forum: Installation &amp; Upgrades
---

### Post by DeadlyChicken on 2009-03-30
Hi there, I am new to Ubuntu having shunned Linux for many years I finally decided that I should give it a go.  and now I feel kinda stupid for taking so long :p

I really like it and its perfect for my laptops which do not have much power and are used mostly for  browsing.

Anyway I decided that it would be cool to get my oldest laptop going, but its too old for boot from usb, and its CD rom has crapped itself.  So PXE network install 

So I did some research and dove in.  Now firstly, my router does dhcp ... can I ignore the dhcp bit and allow my router to keep doing this ? 

( on my first attempt I just turned off the routers dhcp and let the laptop do it as listed in most of the guides I found ) 

anyway the stage I got to was the laptop that I wish to install on, was booting, finding the tftp server, and not finding the file, so I  dug some more and I think I discovered where they needed to be and placed them in there.

then I tried a test on the server machine

tftp localhost -c get pxelinux.0

it returns

tftp: pxelinux.0: permission denied.

can anyone help me out ?

many thanks and sorry if this is already been asked I did search and could not find what I though tI needed.

DC

---

### Post by inobe on 2009-03-30
haven't had the opportunity to PXE boot, i have been eye balling this

[https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)

edit: something more definitive [http://developer.novell.com/wiki/index.php/HOWTO:_Convert_Ubuntu_to_Diskless](http://developer.novell.com/wiki/index.php/HOWTO:_Convert_Ubuntu_to_Diskless)

---

### Post by DeadlyChicken on 2009-03-30
> **inobe said:**
> haven't had the opportunity to PXE boot, i have been eye balling this

[https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)

edit: something more definitive [http://developer.novell.com/wiki/index.php/HOWTO:_Convert_Ubuntu_to_Diskless](http://developer.novell.com/wiki/index.php/HOWTO:_Convert_Ubuntu_to_Diskless)

Thanks, I have a hard disk in the laptop that will be the client, I would like to install Ubuntu to it rather tan run ubuntu as a thin client type thing or a cut down version.

the problem seems to be simply permissions atm.

ok I fix0red it.  I think that I had initially tried a pxe guide that was installing intrepid ? and it wanted me to put the files in a certain place, so I edited the tftpd-hpa file to point to the new location ( from /var/lib/tftpboot/  to /var/www/tftpboot/ ) anyway after a lot of messing about I decided to try putting it back to default and moved teh required files and now it is installing ubuntu on my crappy old laptop.

so far so good, I am happy with that and whats more I think I understand whats going on a bit more now ;)

I did end u p just trying the internet install as I had to go back to work after lunch and so I just left it rather than trying to install directly from a share on the server.

anyway all solved

---

### Post by DeadlyChicken on 2009-03-31
ok so which modules do I install to get what you would get from a Cd install ?? :p

it all installed but it just gave me a command line.

cheers

DC

---

### Post by timcredible on 2009-03-31
why don't you want a thin client?  it works really well and you only have to update the server.  besides, how much memory do you have on that old pc?  if it's less than 512M, ubuntu 8.10 isn't going to work very well, if at all.

---

### Post by DeadlyChicken on 2009-03-31
its got at least 512 MB.

it seems I would need the GNOME desktop a thats what got installed with my ubuntu from the CD.  but its not an option, and the other desktops do not seem to install ( it just gets stuck on 6 percent after selecting one to install )

I think I need to host my own files and hope that gnome is an option if I do that instead of using the internets

---

### Post by DeadlyChicken on 2009-04-01
OK so once you have a command line ubuntu installed its just a case of 

sudo apt-get install ubuntu-desktop

weird thing is, that downloads and installs version 7.something ? 

weird
once in I get an option to upgrade to 8.04, and then I assume 8.10 after that, weird how it doesn't just go for the latest right off the bat ?

Can anyone explain that ?

also looking at how long it took to do the install on command line , that getting stuck at 6 percent was probably downloading the required files or something and had I left it long enough it would have just done it on its own.

---

### Post by triremerufus on 2009-04-03
Greetings,

I've been having a similar problem. I use tftpd32 on a windows box with the intrepid netboot folder ([http://hugi.to/blog/archive/2006/12/23/ubuntu-pxe-install-via-windows](http://hugi.to/blog/archive/2006/12/23/ubuntu-pxe-install-via-windows)), and my machine hangs at the installation of packages no matter how many or how few (including none) I install.

I'm attempting the expert install, and skipped the installation of extra packages, hitting every other item on the list. I'm hoping to install the rest of the packages with something like 'apt-get install ubuntu-desktop' as you have after I complete it. I hope I don't have to dist-upgrade 3 or 4 times like you, DeadlyChicken!

---

### Post by triremerufus on 2009-04-03
That worked. When I got a terminal, I ran the big apt-get for the familiar ubuntu-desktop without dist-upgrade annoyances. I'm currently using synaptic to grab some more of ubuntu-studio.

DeadlyChicken, I really have no idea why your terminal pulled down an old version first, maybe your repositories were set improperly? It is normal to have to go through intermediate versions when doing dist-upgrade. Normal and annoying.

Slightly more information than you might care to have: I'm  pulling a Toshiba Satellite A45-121 out of a drawer to use as a music stand. I've been visiting imslp.org quite a bit, and I want to print as little as possible. The laptop's CD drive failed, and to my knowledge, that machine's bios does not allow USB booting.

---

### Post by DeadlyChicken on 2009-04-05
cool stuff ;) I finally got everythign running properly, the last problem was teh wireless network card ( a belikin PCMCIA 'G' card ) it looked like it was working, but I had two ethernet and two wireless connections listed in network tools, along with an unknown device.

took ages to track it down, but to get it working I had to edit the conf file in /etc/NetworkManager/ to change from false to true, restarted the laptop and bingo I connected to the wifi network.

I am starting to get to grips with this now, likeing it more and more ;)

---

### Post by DeadlyChicken on 2011-07-29
wow its been a while. 

Ubuntu has been working fine for a long time, but just the other day when I booted up firefox will not load.  it just keeps crashing on startup and I have tried all the advices I could find online about resolving the issue ( create new profile, start in safe mode etc ) nothing works it crashes no matter what.  So I figured maybe I would try a reinstall ... But can I figure out how to do this again ?

I have tried following the guides I used last time and it just does not work.  the client machine tries to boot and says "No boot filename received"

---

### Post by jmate24 on 2011-07-30
you need to open this past question with a new thread plz.

---

