---
title: "Getting X to work on first boot?"
date: 2005-11-22
forum: General Help
---

### Post by carlos1 on 2005-11-22
I just managed to install Kubuntu Breezy on a new notebook 
(Acer Travelmate 8100). 
The install went fine until first boot, and after configuring and installing, and getting ready to boot X, the screen went blank. 
I waited for a while but nothing happened. 
I booted into recovery mode and gave the [COLOR="Red"]startx[/COLOR] command as root, but the same thing happened - ie. blank screen. 
I don't know if this is a graphics card problem - I have ATI Mobility Radeon x700 128MB. I've heard ATI cards can be a real B**** with Linux. 
I tried looking through the forum but other people seem to have problems after upgrading from Hoary.  This was a fresh install. 
Can anyone give me an idea of where to look to solve this? 
Thanks.

---

### Post by narcolept on 2005-11-22
what is in /var/log/Xorg.0.log?  There should be an error there (I believe that's the correct filename) that should be able to help out in troubleshooting this.

---

### Post by carlos1 on 2005-11-22
Thanks.
Xorg.0.log is a huge file, I'm not sure what I'm looking for. 
Right at the bottom, it does have: 

"Warning: font renderer for ".pcf" already registered at priority 0"

Then it has the same line repeated, but instead of ".pcf" it says 
.pcf.Z, .pcf.gz, .snf, .snf.Z, .snf.gz, .bdf, .bdf.Z, .bdf,gz, 
.pmf. 

Does this have anything to do with it, or I am looking for something somwhere in the file that actually says "error" at the beginning?

---

### Post by narcolept on 2005-11-22
Wanrings can be ignored most of the time, as it generally is just that, a warning.  If there's no errors whatsoever, there's a chance that your resolution is wrong in /etc/X11/xorg.conf is wrong.  If you can't find an error, rather than searching through use 

```
 cat /var/log/Xorg.0.log |grep -i error 
```

Then I would suggest looking at the config file.

---

### Post by carlos1 on 2005-11-22
Thanks. I used that command and couldn't find any errors. 
In the config file, in the "Screen" section, it does have my resolution (1680x1050) listed, along with various others. 
Is there something specific I should be looking for in the xorg.conf file?

---

### Post by narcolept on 2005-11-23
You should probably paste everything from the video card down from your xorg.conf, check and make sure you're using the right driver.  Before you go pasting, you can always run

```
sudo dpkg-reconfigure xserver-xorg
```

and see if it will autodetect your hardware correctly and possibly start correctly for you. If that fails, paste the config and any pertinant hardware information, someone will probably pick something up. It could also be that your hardware is unsuported. To test that, try the command above, and instead of autodetection, try the standard vesa driver.  If that works, you should get the standard 1024x768, then you know it's an issue with your video hardware and ubuntu. :(

---

### Post by carlos1 on 2005-11-23
I tried dpkg-reconfigure xserver-xorg and switched to the VESA driver, and sure enough, x booted, but only in 1024X768. 
Since this appears to be a driver problem does anyone know of any way with these ATI cards to get the correct resolution (in my case, 1680X1050)?

---

### Post by carlos1 on 2005-11-23
Reading some other posts I got a tip and installed the fglrx drivers (which I had already) but then changed the driver in xorg.conf to "fglrx". 
Now X works, beautiful, but I can't login under username, I get a message 
> Could not read network connection list. 
/home/(user)/.DCOPserver_kubuntu_0
Please check that the "DCOPserver" program is running!
I'll put that in another post.

---

### Post by carlos1 on 2005-11-23
See above

---

### Post by daller on 2005-11-23
I know this can be someway off topic!

Please sum up what problems you have had (and how you fixed them) getting Kubuntu running properly.

Please do one of the following

1. Post it here
2. Send it as a private message to me!
3. Go here: "https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsAcer", and describe problems/how you solved them!

---

### Post by carlos1 on 2005-11-23
There are a couple of things I have fixed so far, which are:
1) Wouldn't boot from Kernel toward the beginning of install. What I did: gave "linux noapi nolapi" as the boot command, which worked. 
2) X wouldn't start after install, which turned out to be a problem with the drivers for my graphics card (ATI Mobility Radeon X700 128MB)., and specifically the screen resolution (1680X1050). 
What I did: installed xorg-driver-fglrx using apt 
```
apt-get install xorg-driver-fglrx
```
That worked and got X running, and at the right resolution.
NOTE: This is already covered in the wiki: 
 [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)
----
I'm having another problem now logging in as a normal user, but that is in a separate post. I'm sure that will besolved shortly as well, then I'll have my beautiful Kubuntu desktop working with no problems.

---

### Post by daller on 2005-11-23
Nice!

Just wanted to know whether or not everything was covered on the wiki page!

Thank you for using Kubuntu :)

---

### Post by carlos1 on 2005-11-23
Yep, and just got the other issue resolved as well, which I'll add to the last post.

---

