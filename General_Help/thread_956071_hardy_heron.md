---
title: "hardy heron"
date: 2008-10-22
forum: General Help
---

### Post by thehappyonebsu on 2008-10-22
I am having trouble with my graphics and audio. My graphics are lagging quite a bit and I can't seem to find the correct way to install a driver that will work for Radeon x300 video card. the information I have found has been a bit vague and only parts of what others have posted have worked. As for my sound some applications have sound others do not and I have no idea why. 
Any help would be appreciated

---

### Post by dileepdinesh on 2008-10-22
drivers for ati radeon cards can be installed from "add or remove programs"....just search with term "radeon", drivers would come up,,, mostly it should solve ur problem,,,but if ur card belongs to those ati radeon cards with no supported drivers from ubuntu,then the best way is to download the binary files from the manufacturer (amd) itself, and make the package ur way,,,(the last method is more sure to work,but takes time to compile and built package)

As for ur audio, if u could mention the applications for which the sound do not work, i might be able to help u,,i think i had same kind of problem,,(even now i do have it)..do you try to use two players at the same time,like vlc and default movie player at the same time?,

---

### Post by thehappyonebsu on 2008-10-22
as for the video drivers I have not been able to get anything from the add remove the card I have is supported but I am having a lot of trouble with the graphics still I was trying to use [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
the section on manually installing from ati.com but when it says things like

 You will then need to build the installation packages with the downloaded ATi drivers (ensure the ATi drivers have the execute flag set first): 

I don't know how to do that

---

### Post by thehappyonebsu on 2008-10-22
the main problem I am having is that my refresh rate is slower than it should be so the images are constantly lagging. it all started at the same time config-2.6.24-21-generic appeared on my boot screen

---

### Post by dileepdinesh on 2008-10-23
i think setting the execute flag is easy,say ur driver is "mydriver.bin"
then to set execute flag the command would be
>>chmod a+x mydriver.bin
then to execute it 
>>./mydriver.bin
this should build the packages with dpkg extension.( i guess for ur binary file, 
there will be many packages
to install a package .dpkg extension its enough to directly double click the file
it will be automatically installed
 As for ur refresh rate try System->preferences->Screen resolution, it has a option for refresh rate...it might work
if ur finding problem with the new kernel installation (2.6-24-21-generic),then why dont u continue using 2.6-24-19-generic,moving down the boot menu , u can find this..(i am also having problem with this new kernel thing),hope this helped
u,,,

---

### Post by thehappyonebsu on 2008-10-23
Sorry I should probably be more specific I know how to set the flag I just don't know what I need to have downloaded and where it should be.  i have changed the refresh rate in the resolution area it just isn't working well which is why I think its a driver problem.    Also thank you everyone who has replied I really appreciate the help

---

