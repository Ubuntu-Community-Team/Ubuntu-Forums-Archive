---
title: "How to enable Desktop Effect on Optimus laptop?"
date: 2011-02-06
forum: Hardware
---

### Post by bathou on 2011-02-06
Hi,

I have an ASUS U36 laptop which has Intel i915 and Nvidia G310m.

I installed the Nvidia official driver for the CUDA, but
did not let it modify my xorg.conf.

The Desktop Effect could not be enabled though CUDA works ok.


Is there any way to utilize i915 for desktop effect?

Thanks a lot.

---

### Post by Storm Aiden on 2011-02-07
In previous versions of Ubuntu, if you wanted wobbly windows and eye  candy, you had to follow complicated HowTos full of a lot of copying and  pasting of cryptic commands, with the very real possibility of you  screwing up your graphics configuration to the point where it's  unusable. 
 Now (as of 7.10) Ubuntu allows you an easy way to enable desktop  effects. Keep in mind that you may have to enable proprietary video card  drivers if you have an Nvidia or ATI video card. See an example of this  (using Nvidia as an example) [here]("http://www.psychocats.net/ubuntu/nvidia"). 
   [[IMG]http://www.psychocats.net/ubuntu/images/desktopeffectsthumb01.jpeg[/IMG]]("http://www.psychocats.net/ubuntu/images/desktopeffects01.png") 
Go to **System > Preferences > Appearance** 
  [[IMG]http://www.psychocats.net/ubuntu/images/desktopeffectsthumb02.jpeg[/IMG]]("http://www.psychocats.net/ubuntu/images/desktopeffects02.png") 
In **Appearance Preferences** select the **Visual Effects** tab. 
  [[IMG]http://www.psychocats.net/ubuntu/images/desktopeffectsthumb03.jpeg[/IMG]]("http://www.psychocats.net/ubuntu/images/desktopeffects03.png") 
Then, select **Normal** or **Extra**, depending on how fancy you want your desktop effects to be. 
  [[IMG]http://www.psychocats.net/ubuntu/images/desktopeffectsthumb04.jpeg[/IMG]]("http://www.psychocats.net/ubuntu/images/desktopeffects04.png") 
Ubuntu will try to enable desktop effects. If the trial works, you  should see this dialogue, and you can decide to keep the newly enabled  effects or revert back to having no desktop effects. 
  [[IMG]http://www.psychocats.net/ubuntu/images/desktopeffectsthumb05.jpeg[/IMG]]("http://www.psychocats.net/ubuntu/images/desktopeffects05.png") 
If the trial doesn't work, you'll be told *Desktop effects could not be enabled*, which may mean that you don't have the proper video drivers installed or that your video card cannot support desktop effects. 
 If you're having trouble setting up desktop effects, please search or post a support thread in [Desktop Effects & Customization subforum of the Ubuntu Forums]("http://ubuntuforums.org/forumdisplay.php?f=223")

---

