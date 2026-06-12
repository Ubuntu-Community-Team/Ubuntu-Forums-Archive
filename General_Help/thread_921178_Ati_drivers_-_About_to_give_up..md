---
title: "Ati drivers - About to give up."
date: 2008-09-16
forum: General Help
---

### Post by Alfx on 2008-09-16
I finally decided to make the switch to unbuntu.

Im using unbuntu hardy heron

I was kinda disappointed to see the max resolution I could use was 1240X1080(something like that)

I normally use 1680X1050.

I tried to install the ATI drivers, but I horribly failed.

I have looked at the guide that is here: [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Follow_These_Instructions_Carefully](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Follow_These_Instructions_Carefully)

-I think I have installed the ATI drivers successfully

-They do not work

-When I type "fglrxinfo", it tells me that its using the mesa drivers

-I tried to uninstall the mesa drivers, it doesnt seem to work and the fglrx doesnt seem to want to use the ATI drivers instead.

-I can only run unbuntu in low graphic mode now for some reason(which is god aweful)

Please someone help me!

---

### Post by ktechman on 2008-09-16
Have you edited your xorg file??? One other thing ENVY will install and configure a working xorg file for you and install the drivers correctly. System/Administration/Synaptic Package Manager search for envyng-gtk (GTK extension for Gnome desktop and envy-qt for kde)  Gnome looks more like windows and installs by default in a stock ubuntu install.  Install and then go to Applications/System Tools and open ENVY choose the ATI driver and you are off to the races.

---

### Post by Alfx on 2008-09-16
> **ktechman said:**
> Have you edited your xorg file??? One other thing ENVY will install and configure a working xorg file for you and install the drivers correctly. System/Administration/Synaptic Package Manager search for envyng-gtk (GTK extension for Gnome desktop and envy-qt for kde)  Gnome looks more like windows and installs by default in a stock ubuntu install.  Install and then go to Applications/System Tools and open ENVY choose the ATI driver and you are off to the races.

I edited the xorg file exactly like they said in the guide, but it didnt seem to change anything.

I also tried Envy, but it was saying my card wasnt compatible with the drivers.

I have an Ati radeon 4870

---

### Post by ktechman on 2008-09-16
They are recommending the ATI 8.8 driver which has poor support under Linux at the moment do you have an old card to use until the driver gets support under Linux??? [http://forums.amd.com/game/searchresults.cfm?requesttimeout=500](http://forums.amd.com/game/searchresults.cfm?requesttimeout=500)  here is my source.

---

### Post by Alfx on 2008-09-16
> **ktechman said:**
> They are recommending the ATI 8.8 driver which has poor support under Linux at the moment do you have an old card to use until the driver gets support under Linux???
Unfortunately no,
Its the only card I possess.
[IMG]http://ubuntuforums.org/images/smilies/icon_sad.gif[/IMG]

---

### Post by ktechman on 2008-09-16
I am actually in this forum looking for support for my ATI card, what a learning experience.  I will definitely look twice before I jump onto the ATI bandwagon again.  The only reason I did purchase a laptop with ATI graphics is because of the 8xxx and 9xxx series Nvidia graphics cards are dropping like flies who knows if down the road after the warranty is up if they will give me a new motherboard or make up some lame excuse that you waited one week or day to long and then what? Kind of a catch 22.

---

### Post by Alfx on 2008-09-16
> **ktechman said:**
> I am actually in this forum looking for support for my ATI card, what a learning experience.  I will definitely look twice before I jump onto the ATI bandwagon again.  The only reason I did purchase a laptop with ATI graphics is because of the 8xxx and 9xxx series Nvidia graphics cards are dropping like flies who knows if down the road after the warranty is up if they will give me a new motherboard or make up some lame excuse that you waited one week or day to long and then what? Kind of a catch 22.

Its my first Ati as well.

The only reason I bought an ATI card was because the of the price/performance compared to the Nvidia ones.

---

### Post by ktechman on 2008-09-16
You know you could be waiting until after Christmas for a stable driver ATI is as slow as molasses!

---

### Post by Alfx on 2008-09-16
> **ktechman said:**
> You know you could be waiting until after Christmas for a stable driver ATI is as slow as molasses!

How will I know when Ati drivers are stable for linux?

---

### Post by ktechman on 2008-09-16
The only way I know of is to keep checking the forums and continue to ask.  The ATI forums may be of some help but don't hold your breath.  I am not sure why ATI chooses not to support anything they can get there hands on considering their bleak financial situation.  I think they have posted large losses lately.  Just doesn't make sense.

---

### Post by rmjohnson144 on 2008-09-16
> **ktechman said:**
> The only way I know of is to keep checking the forums and continue to ask.  The ATI forums may be of some help but don't hold your breath.

I just downloaded and installed the 8.8 drivers off their website and followed their instructions and it worked flawlessly.  So far I haven't been able to fully test them and my movies are playing back better than before, but they flicker badly in windowed mode, but if you go full-screen, they look beautiful.

What are some good 3d stuff to test with.  So far this card (3870) is working slightly better than my other card (8800GT).

I just downloaded the driver to my desktop.
[http://ati.amd.com/support/drivers/linux64/linux64-radeon.html](http://ati.amd.com/support/drivers/linux64/linux64-radeon.html)

Then right clicked the ati-driver-installer-8-8-x86.x86_64.run file and selected properties and set it to executable.

Then I went into terminal mode and changed my directory to desktop.  typed in,"sudo sh ati-driver-installer-8-8-x86.x86_64.run"  and chose to auto install.  

When finished I typed in sudo aticonfig --initial

then exit out of the terminal and reboot and viola it seemed to work like a champ so far.  at least it didn't give me the white screen of death anymore. - lol

Link to the ATI install docs:
[http://ati.amd.com/support/drivers/linux64/linux64-radeon.html](http://ati.amd.com/support/drivers/linux64/linux64-radeon.html)

Good luck
-=Mark=-
ps. I forgott to add to uninstall the old drivers first.  If you used Envy, it should have an uninstall method you should try first.

---

### Post by ktechman on 2008-09-16
After I finished the install with the 8.5 driver I experienced the same video problem. It seems as if all they have done is wrapped the same driver up in another package.  As a matter of fact when I experimented with Vista and this driver Windows had to shut down Aero to show the video, and this card is supposed to be able to access just over a Gig of memory! (256 on-board) I have a 7 year old Nvidia card with 64mb of ram that will perform almost as well as this ATI card.  Go figure that one out.  Unless this card can do two things at once like openGL and video it is no better that the onboard graphics we have all been used to in he past.  :(
I have read some of the posts on the ATI forum and they are pretty unfriendly, the senior admins act like Linux is the problem. I believe it is just a case of misdirection so we look at the OS instead of the driver.  BTW the ATI wiki needs an update in the worst way they are still referencing Gutsy, most of us are looking forward to Intrepid.  Where did Hardy go?????

---

### Post by Alfx on 2008-09-16
> **rmjohnson144 said:**
> I just downloaded and installed the 8.8 drivers off their website and followed their instructions and it worked flawlessly.  So far I haven't been able to fully test them and my movies are playing back better than before, but they flicker badly in windowed mode, but if you go full-screen, they look beautiful.

What are some good 3d stuff to test with.  So far this card (3870) is working slightly better than my other card (8800GT).

I just downloaded the driver to my desktop.
[http://ati.amd.com/support/drivers/linux64/linux64-radeon.html](http://ati.amd.com/support/drivers/linux64/linux64-radeon.html)

Then right clicked the ati-driver-installer-8-8-x86.x86_64.run file and selected properties and set it to executable.

Then I went into terminal mode and changed my directory to desktop.  typed in,"sudo sh ati-driver-installer-8-8-x86.x86_64.run"  and chose to auto install.  

When finished I typed in sudo aticonfig --initial

then exit out of the terminal and reboot and viola it seemed to work like a champ so far.  at least it didn't give me the white screen of death anymore. - lol

Link to the ATI install docs:
[http://ati.amd.com/support/drivers/linux64/linux64-radeon.html](http://ati.amd.com/support/drivers/linux64/linux64-radeon.html)

Good luck
-=Mark=-
ps. I forgott to add to uninstall the old drivers first.  If you used Envy, it should have an uninstall method you should try first.

-I finally managed to get the ATI drivers installed properly.

-I enable the drivers in system->administrator-> hardware drivers, but after I rebooted, I'm forced to run in low graphic mode!

-The catalyst control center doesn't work either!


What I am supposed to do now?

---

### Post by Alfx on 2008-09-16
Bump

---

### Post by Alfx on 2008-09-16
Dump

---

### Post by rmjohnson144 on 2008-09-16
> **Alfx said:**
> -I finally managed to get the ATI drivers installed properly.

-I enable the drivers in system->administrator-> hardware drivers, but after I rebooted, I'm forced to run in low graphic mode!

-The catalyst control center doesn't work either!


What I am supposed to do now?

I had the same issue.  it seems that enabling that forces new drivers to be installed and I'm not sure they're ATI drivers or not.

I finally figured out how to get out of the low res mode.  Mine was stuck in 640x480 and most of my menus were cut off and I was unable to install anything as I was unable to click continue or next or whatever it want.

I finally rebooted and hit esc to enter the grub menu and boot into recovery mode and all was reset back to normal resolution.  I then rebooted back to regular boot mode and all was fine.  3D stuff is still flakey as hell.  I'm thinking these drivers work well for 2D stuff, but 3D stuff just doesn't cut the muster!

currently I disabled the hardware version and used the envy version.  I haven't tried this method with any other driver yet.  I may reinstall my 8800GT and see if I get any better results.

Good luck.
-=Mark=-

---

