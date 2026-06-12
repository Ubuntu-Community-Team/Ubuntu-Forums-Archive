---
title: "hp pavilion dv6 laptop overheating. tried various solutions."
date: 2013-03-06
forum: Hardware
---

### Post by malapradej on 2013-03-06
Hi,

I have an hp pavilion dv6 with ATI radeon graphics card. The cpu is currently at 70 degrees idle and gpu at 90 idle!!!!!!!! I have paid for a proper cleanup (£60 later) including fans and thermal paste etc. I have tried:

1. the Jupiter app which is supposed to adjust the power usage.
[http://www.webupd8.org/2011/04/jupiter-0050-released-fixes-restore.html](http://www.webupd8.org/2011/04/jupiter-0050-released-fixes-restore.html)
2. checked the bios is the latest version.
3. edited /etc/default/grub to include 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force"4. installed the proprietary drivers ( only can't monitor gpu then... )

with temperatures staying the same... All the above were suggested on this forum and others.

Any advice will be much appreciated.

Jacques.

---

### Post by malapradej on 2013-03-06
Anyone. Please! I have just edited the temperatures..... Its going up....

---

### Post by Linuxisfast on 2013-03-06
Have you installed the proprietary hardware drivers via the applet? Usually the ATI drivers make the CPU run cooler.

---

### Post by mörgæs on 2013-03-06
Please stop bumping your threads.

---

### Post by malapradej on 2013-03-06
Hi Linuxisfast. Thanks for the feedback. I have removed the ATI driver and installed the Radeon driver. The terminology is new to me but I suspect the ATI is the proprietary driver and Radeon the open-source driver. I tested bot and temp was high either way. Difference was that I could not find a way to monitor the GPU temp with ATI installed. I would be pleased if you could point one out, before I reinstall the ATI driver. Neither psensor nor jupiter or one of the command line tools such as "sensor" worked. 

To mörgæs: Apologies if this irritated you. It's just that the temperature had gone up shortly after I posted and I would have liked to include this. Did not mean to ruffle the cats tail ;)

---

### Post by malapradej on 2013-03-06
Thanks for the advice. That did the trick. Just a note for those who have the same problem. I downloaded installed the AMD catalyst driver as per instructions:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
Using method in section 3. and downloading driver from:
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
After ```
sudo aticonfig --initial
``` I had an error about not being able to stat a switchlibGL and switchlibglx file in /usr/lib64/fglrx/. I just moved the files in the /usr/lib/fglrx/ location to lib64 and then run the command again. They are both python scripts. I had a look at both and they can distinguish between 64 and 32 bit systems, so works exactly the same for both.
Now I have a quiet and cooler laptop. Only problem is I can't seem to monitor the GPU temperature. CPU is at a significantly cooler idle temp of 48-54 degrees.

---

### Post by malapradej on 2013-03-07
OK. Now it starts again...
I tried to switch over to the intel gpu as explained in:
[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)
using:
sudo aticonfig --px-igpu[FONT=Arial][/FONT]
now I cant log in. It keeps looping back to the login screen. 
I have tried various solutions:
1. removed xorg.conf
2. sudo startx
3. removed .X0-lock
4. reboot. Nothing helps.
fglrxinfo comes up with:
Error: unable to open display (null)
Trying to find solution but struggling....

---

### Post by internazi on 2013-03-07
HP had some lawsuits thrown at them because they couldn't build laptops that didn't fry. If you really like that comp the fix is about $175. It isn't going to heal itself and it isn't a software fix.

---

### Post by malapradej on 2013-03-07
Thanks Internazi,
If only I knew when I bought it. Unfortunately I am stuck with the lady, and she needs attention. When running on the discrete driver it seemed to work better. I guess I should have left it there. I tried to swap to the intel gpu and my woes have started again. Please tell me your going to help me get her back to work again. 
I have tried the reinstallation process, but now it comes up with:
```

$ sudo aticonfig --initial -f
X11 connection rejected because of wrong authentication.
X11 connection rejected because of wrong authentication.
X11 connection rejected because of wrong authentication.
X11 connection rejected because of wrong authentication.
Uninitialised file found, configuring.
PowerXpress error: Cannot stat '/usr/lib64/fglrx/switchlibGL': No such file or directory
Failed to initialize libglx for discrete GPU
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.original-7

```
I can try to cp or ln the switchlibGL from /usr/lib/fglrx. This worked last time. Although the ```
X11 connection rejected because of wrong authentication.
```error is a mystery to me. Help still very much needed here...

---

### Post by malapradej on 2013-03-07
Ok. Now I managed to get a desktop running. I used the advice in [http://cisight.com/install-amd-radeon-hd-6470m-and-solve-overheat-on-ubuntu-1110-oneiric/](http://cisight.com/install-amd-radeon-hd-6470m-and-solve-overheat-on-ubuntu-1110-oneiric/) although Unity is not working. All I get is a background image and icons. No panel. 
I edited my xorg.conf file to look like his and ran "sudo lightdm restart". Running "sudo startx" still comes up with```

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.


Please consult the The X.Org Foundation support 
         at http://wiki.x.org
 for help. 

 ddxSigGiveUp: Closing log
X connection to :0 broken (explicit kill or server shutdown).

```

---

### Post by malapradej on 2013-03-07
I am really so frustrated. I have been at this for the last 2 days and there seems to be no answer. The best I got is a suggestion that HP laptops are the problem. The laptop has worked before. Surely there must be someone out there that knows how to fix this. I am starting to see why people are going for other distros or moving back to windows. I love ubuntu, and have tried to promote it to everyone I know. Recently installed it for a friend who is now convinced that it is the solution to his windoze problems. I am starting to loose faith here people. Help me out..... Please.... Community... UBUNTU....

---

### Post by malapradej on 2013-03-07
The sad case of me answering myself again! Oh well, I am an only child. sic!

Help came from various forums. 
1. The following page has a section about installing the Intel driver. Added the repository and updated software.
[http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error](http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error)
Following this I could get in to the welcome login loop. i.e. I login and and I login and I login and I login.... OK, I did not really login 4 times in a  row, but it would have kept on asking me to login and returns to the login screen. I much prefer this to the "blah ... low graphics mode ... blah" screen which just stares at me.
2. [UbuntuNooBkjp]("http://askubuntu.com/users/68940/ubuntunoobkjp") gave some advice for the "loopy the loop" screen above.
[http://askubuntu.com/questions/146137/login-screen-loops-unless-you-login-as-guest](http://askubuntu.com/questions/146137/login-screen-loops-unless-you-login-as-guest)
```
sudo mv .Xauthority .XauthorityBak
```
does the trick together with a reboot. 
I can now login and have a working desktop. CPU temp is back to 63 degrees. How am I ever gonna sort this out?!

---

### Post by malapradej on 2013-03-08
At long last overheating has been curbed and can make a choice between gpu's to use. I followed the advice on these sites:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)
[http://asusm51ta-with-linux.blogspot.co.uk/](http://asusm51ta-with-linux.blogspot.co.uk/)
Basically remove fglrx/proprietary drivers completely, then install open-source radeon drivers and intel driver through ppa, then get vgaswitcheroo to work including the script in the last page.

---

### Post by sacrificial anode on 2013-05-08
I wanted to write up my fix after solving my DV6 overheating issue. I hope it helps someone out, coz it gave me hell for the last 6 months.- super noisy fan, quickly overheating, too hot to rest on my lap, and finally my first "thermal-shutdown".
After searching the web and trying to find software issues, I was still convinced that it was a physical blockage in the cooling system.
I decided to get in there and dig around. I watched this video
[http://youtu.be/M7CEtfJtu_Y](http://youtu.be/M7CEtfJtu_Y)
then pulled it apart.

i blew air through the fan/fins, dusted it out and put it together to no avail.
Still unconvinced, I stripped it down again and I found that the "radiator-like" fins were almost completely blocked where the fan blows out- against it.
I used a long, thin needle to poke right-through the fins and into the fan area which broke away a lot of really-fine, compacted dust in the fan-blade area. after some thorough, blowing, brushing and poking, I clipped it all back together.

Finally, she runs whisper quiet again!! There's actually cool air flowing freely in and out of the vents. now the CPU, and hole laptop-structure runs so much cooler.

Hope this helps you and many others.

Cheers

---

