---
title: "HP Paviliion Dv6 no sound headphones"
date: 2009-07-22
forum: Hardware
---

### Post by gufur on 2009-07-22
This is the history of my attempt to  get sound on my HP pavilion DV 6 with AMD 64 processor.

I started off with an old installation of ubuntu updated to 9.04. Below are my attempts described.

Step 1.
Background. 
New laptop HP pavilion DV6. Ubuntu 9.04 on ext HD. When I started up on the new laptop I had no sound at all. I got the sound main speakers going by doing 
sudo gedit /etc/modprobe.d/alsa-base.conf
and added at the bottom 
options snd-hda-intel model=hp-m4 
or 
options snd_hda_intel model=hp-dv5
both works.
BUT my headphones does not work at all. I have tryed several solution from Internet and forums but none worked.
I found under comunity documentation the sound troubleshooting page 
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting).
Following that instruction I found out that my codec as indicated when running 
wget -O alsa-info.sh [http://alsa-project.org/alsa-info.sh](http://alsa-project.org/alsa-info.sh) && bash ./alsa-info.s
is 
!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: IDT 92HD75B3X5

Now comming to the problem. The instruction tell me to find that codec in 
ALSA-Configuration.txt file. which for my driver revision is
[http://git.alsa-project.org/?p=alsa-kmirror.git;a=blob;f=Documentation/ALSA-Configuration.txt;h=f9d11140af913c95d317963d9b0c1bd672a881ef;hb=93fd148a2250de218a5e3642cb41329132dd01fe](http://git.alsa-project.org/?p=alsa-kmirror.git;a=blob;f=Documentation/ALSA-Configuration.txt;h=f9d11140af913c95d317963d9b0c1bd672a881ef;hb=93fd148a2250de218a5e3642cb41329132dd01fe) 

But I cant find that codec at all ????
So what do I do now ?

/Gunnar

Step 2

PS 26 July 2009
A small correction: 
options snd-hda-intel model=hp-m4 does not work fully out. The sound and mic does not work properly when using Skype.
Conclusion: the only fairy working option is 'options snd_hda_intel model=hp-dv5'. that is, exept for the non working headphones.

Step 3

PS 3 Aug 2009
Ubuntu 9.04 was updated around 1 aug. From that date I cant get any sound not in main speaker nor in earphones. I tried to use the pulse server as described in "Sound Solutions for Ubuntu 9.04 (Jaunty) Users" as described in 
[http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html#more-1301](http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html#more-1301)
I can track the sound to the PulseAudio applet. How do I route it from there to the speakers.

Step 4

PS 4 17 Aug 2009 
I am giving up with ubuntu on my laptop. I have tryed everything ( i think) It is very sad because I like most of whats un UBUNTU. The thouch of windows on a base of UNIX most of it is pretty simple to handle but the sound issues seem to be so complicated so no one understand how to get it working. Is there any structure at all???
Some history. 
I put ubuntu on a ext hd working from my old HP and U 8.10. Everything worked perfect. I changed to new laptop HP pavilion dv6 about the same time as I upgraded to 9.04. From that time the sound has been working in main speakers of  and on with a bit of  "hacking" (thanks to all the treads I have been trough). From the last upgrade package I have had no sound at all. No matter how much I used "the threads".  I last attempt was to clear all ubuntu and install it all from the beginning, from the CD.  Still no sound. I tried to install medibuntu as described in [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683). Still no sound

I am giving up now..... A successfull OS must not have all these problems with a so basic feature as the sound.  If I only coud blame my laptop brand but HP is a very large manifactor of laptops.
As stated above It is sad.   Goodluck in the future but I can not spend this many hours on such a basic issue.

Step 5

I just don't want to give up... I bit stubborn.. (well not just a bit)


This is how I finally solved it. 
I have sound on main speakers and on the headphones. There is just one problem left but it is not much of a problem. The main speakers are not disconnected when I plug in the plug for headphones.


I reinstalled ubuntu from a disk. just to get a fresh start.

1. follow 
get the basic sound scheme properly set up for optimum use according to 
[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

2. change alsa driver version to the latiest one according to 
[http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/)

3 Edit the... sudo gedit /etc/modprobe.d/alsa-base.conf ... according to 
[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)
I used 
"options snd_hda_intel model=hp-dv5"
If that one does not work test other solutions from all the added on comments from verious persons
Here I got the main speakers working but no headphones

4 To get the headphones working Open the "Gnome Alsa-Mixer" (application/ sound and video)
Check the Import0 and set the Import0 (Can be Import1, test which one works for you)  volume on max.
if the mainspeakers did not work, make sure the speaker and Master box is UNCHECKED

---

