---
title: "Can't install Adobe AIR 1.5"
date: 2009-08-01
forum: Installation &amp; Upgrades
---

### Post by diniox on 2009-08-01
I had Ubuntu 8.10 with Adobe AIR 1.5 and I upgraded to 9.04. After I use computer-janitor and remove all proposed packages. It remove all AIR applications (from /opt) and remove Adobe AIR. When a install Adobe AIR 1.5 i see:
```
An error occurred while installing Adobe AIR. Installation may not be allowed by your administrator. Please contact your administrator.
```
And installation is abored but in /opt where are Adobe AIR/Versions/1.0 etc. In menu there aren't any AIR icons and Synaptic tell that adobeair1.0 package damaged and must do sudo apt-get install -f . When I entered sudo apt-get install -f adobeair1.0 package is remove. Second package abobe-certs is good.
How can I repair it? How can I install Adobe AIR 1.5?

---

### Post by running_rabbit07 on 2009-08-10
> **diniox said:**
> I had Ubuntu 8.10 with Adobe AIR 1.5 and I upgraded to 9.04. After I use computer-janitor and remove all proposed packages. It remove all AIR applications (from /opt) and remove Adobe AIR. When a install Adobe AIR 1.5 i see:
```
An error occurred while installing Adobe AIR. Installation may not be allowed by your administrator. Please contact your administrator.
```And installation is abored but in /opt where are Adobe AIR/Versions/1.0 etc. In menu there aren't any AIR icons and Synaptic tell that adobeair1.0 package damaged and must do sudo apt-get install -f . When I entered sudo apt-get install -f adobeair1.0 package is remove. Second package abobe-certs is good.
How can I repair it? How can I install Adobe AIR 1.5?

Do you have root privileges? You need to set that up to install.

---

### Post by RobMagus on 2009-08-23
I'm having the exact same problem.

I had installed Adobe Air and tWhirl several months ago, and twhirl was running fine.  I ran an upgrade to the latest Linux kernel, then ran the janitor, and it removed some unused .debs - among them adobeair1.0 and twhirl.

When I restarted, twhirl looked like it had been removed completely, so I went to the twhirl website [http://www.twhirl.org/](http://www.twhirl.org/) to reinstall.  The installer is supposed to automatically install air 1.5, but it throws the error diniox gets (although a few times it's just thrown a general error, something like "installation could not be completed, please try again").

At this point there's an error icon in the gnome panel, and on mouseover it reads:

"An error occured, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was: ' Error: BrokenCount > 0'This usually means that your installed packages have unmet dependencies"

I click on it and it opens the update manager, which says it can only run a partial upgrade. I tell it to do say, and it says it will remove adobeair1.0, which I allow. This appears to work fine.  But I've gotten nowhere!

At this point, the whole process can be repeated - I try to install twhirl, the installer throws an error when installing air1.5, the package manager wants to run a partial upgrade to remove air1.0, it does so.

I'm guessing that either adobeair1.0 isn't being removed properly, or that the latest kernel upgrade (which diniox would have done too, as he just upgraded to 9.04 last week) screws with air somehow.

Please help!

---

### Post by rustymh on 2009-09-01
I have exactly the same problem after running the Computer Janitor.

"An error occurred while installing Adobe AIR. Installation may not be allowed by your administrator. Please contact your administrator."

I have even enable Administrator Login, logged in as root and that didn't even worked.(same error)

I am at the point of reinstalling ubuntu, but hoping for a solution before I do that.

Searched the internet for a solution for 5 days now.

---

### Post by rjpilla on 2009-09-07
anybody figure this out having same problem after using computer janitor. When I try to install it leaves adobe air as broken in synaptic.

---

### Post by rjpilla on 2009-09-07
SOLVED!! Delete the adobe-cert package from synaptic. If not there check the etc/opt folder and delete the Adobe folder. Air will install after this. Make sure you did complete removal of broken package also from your previous tries. Enjoy

---

### Post by rodmond on 2009-09-09
> **rjpilla said:**
> SOLVED!! Delete the adobe-cert package from synaptic. If not there check the etc/opt folder and delete the Adobe folder. Air will install after this. Make sure you did complete removal of broken package also from your previous tries. Enjoy

Brilliant!  This worked 100% for me!  Thank you, thank you!

---

### Post by ferric84 on 2009-09-18
that didn't work for me because I manually deleted all traces I could find of anything Adobe/AIR releated, but finally fixed it with this command:

```
sudo dpkg --purge adobe-certs
```

what a pain this whole process was.

---

### Post by LaneLester on 2009-09-20
I didn't have any trouble installing AIR, but then it's not able to install any apps. The install of an app proceeds to where you click Open or Save. If Open, the process dies quickly. If Save and then install the saved file, that process dies quickly. I'm running Karmic A6 now, but the problem developed with Jaunty.

Lane

---

### Post by El_Perro_Perduto on 2009-10-04
...Same problem:  Used the Computer Janitor; it messed up Air.  Uninstalled adobe-certs and reinstalled Air successfully.  Now I cant install the ikitesurf.air (wind monitoring app for kitesurfers).  Pull down menu includes an Adobe Air app installer, but nothing happens when I try and launch the utility.  Pls help.

---

### Post by leoyde on 2009-10-30
Thanks ferric, thats exactly what I needed... pain indeed!

---

### Post by boyevil on 2009-11-05
> **ferric84 said:**
> that didn't work for me because I manually deleted all traces I could find of anything Adobe/AIR releated, but finally fixed it with this command:

```
sudo dpkg --purge adobe-certs
```

what a pain this whole process was.

thanks, i was at two hours when i found this. Awesome!!!

---

### Post by Neovos on 2010-04-26
> **ferric84 said:**
> 

```
sudo dpkg --purge adobe-certs
```

what a pain this whole process was.

Same problem, can confirm this fix also. Nothing showed up in synaptic and nothing worked till I did this.

---

### Post by odd on 2010-07-28
And what if I don't have adobe-certs in synaptic? It's Lucid 64bit.
I have installed AIR2.0 from Adobe website (deb 32bit), worked like charm, installed iPlotz and Boks, they're both working good, and then out of the sudden, I can't install any other AIR apps via web browser and Synaptic tells me this 'BrokenCount > 0' error and wants to remove iPlotz and Bloks in order to fix this.

---

### Post by pterosky on 2010-09-07
I installed balsamiq mockups for desktop Version 1.8.12, but am also getting the 'Error:BrokenCount > 0' message. I

In Synaptic there is a broken package: balsamiqmockupsfordesktop

---

### Post by kylea on 2010-09-20
I installed balsamiq mockups for desktop Version 1.8.12, but am also getting the 'Error:BrokenCount > 0' message. 

>> Getting the same error - confused

---

