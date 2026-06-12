---
title: "special key(bindings)"
date: 2008-03-27
forum: Hardware &amp; Laptops
---

### Post by krang on 2008-03-27
Hi there,

I just added some custom keybindings in the gnome config editor for switching my screens with xrandr (xrandr --output VGA-0 --off --output LVDS --mode 1280x800 e.g.) and binded it to <super>F7. This really works very well...

But I want to use this special key next to the super-key instead. I think you know this button with the tiny name "FN". It just makes more sense to me, because that's the way, my keys are sgined on my keyboard... The keybinding <fn>F7 doesn't work so I just ask for some kind of "name" of this button.

I'm using (and testing) 8.04 which is working very very well for me :)

Thanks

---

### Post by benste on 2008-03-27
Can you see a key generated when you use the FN + F7 in the grafical shortcut thing of gnome?

+ You've got a intel card right? can I use this XRAndr ...  also for an nvidia card- I normally use nvidia -settings, but I always takes a bit of time :(

---

### Post by krang on 2008-03-27
I do not see anything happen while pressing the FN-Button. It works well with decreasing or increasing brightness, But I don't see anything who configured that? Is it Hardware??

benste: it's told on the xRandR-Page that you can also use it with nvidia-cards: [Debian-Source](http://wiki.debian.org/XStrikeForce/HowToRandR12) and with my aticard e.g. ;)

---

### Post by benste on 2008-03-27
No, for Sony Vaio models  they always tell that it is a misconfigured ACPI or something els
I hope someone can help you

What model do you have, also a Vaio? Than lookinto the special "calling all vaio owner thread"
Someone is trying to make some software to configure those things.

---

### Post by krang on 2008-03-27
Ok then, let's have a look :) thanks so far.

I'm using a VGN-A115Z with a ati mobile radeon 9200 (give me driver problems everytime.....)

---

### Post by benste on 2008-03-27
use envy to install grafic driver :-)
here are the links:
 do :

[http://ubuntufs.wordpress.com/2007/06/09/attention-all-vaio-owners/]("http://ubuntufs.wordpress.com/2007/06/09/attention-all-vaio-owners/")

post in:
[http://ubuntuforums.org/showthread.php?t=465491&highlight=install+ubuntu+sony]("http://ubuntuforums.org/showthread.php?t=465491&highlight=install+ubuntu+sony")

and try:
[http://ubuntufs.wordpress.com/2007/03/06/special-keys-tutorial-part-1/]("http://ubuntufs.wordpress.com/2007/03/06/special-keys-tutorial-part-1/")





Thank you for XRandr and shortcut clue (I'm using it with smartdimmer and try to use xrandr later:)

---

### Post by benste on 2008-03-27
Can you give me a clue how to use XRANDR ?

> benste@VAIOFe31m:~$ xrandr
Screen 0: minimum 320 x 240, current 1280 x 800, maximum 2560 x 1024
default connected 1280x800+0+0 0mm x 0mm
   1280x800       50.0*    62.0  
   1152x768       51.0  
   1024x768       52.0  
   800x600        53.0     54.0  
   640x480        55.0  
   640x384        56.0  
   576x384        57.0  
   512x384        58.0  
   400x300        59.0     60.0  
   320x240        61.0  
   2560x1024      62.0  



normally nvidia-settings
Recognize 2 DVI (internal flat panel + out VGA adapter)
and a S-video also out

seems not be regonized here or like
[http://wiki.debian.org/XStrikeForce/HowToRandR12]("http://wiki.debian.org/XStrikeForce/HowToRandR12")??


[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2")
>   Supported drivers

Ubuntu 7.10 Gutsy Gibbon

    * X.org intel driver, version ??? (included in Xorg ???) and later. Ubuntu version: 2:2.1.1-0ubuntu2 with xrandr 1:1.2.2-0ubuntu1 

    * X.org radeon driver, 6.7.192 and later (in ubuntu gutsy and hardy, but they still have very serious issues for some Thinkpads). 


seems not to work for mine?=

---

### Post by duo001 on 2008-03-30
The Fn key is only used on laptop model computers. It ties in with hardware, so it only works to do the functions listed on the function keys. 
The way the Fn key works, is it allows one key to do two jobs. In the case of your F7 key, when holding down Fn+F7 it changes your screen brightness. You are unable to change this as it is hard-coded into the core of the system itself.

---

### Post by benste on 2008-03-30
My FN keys aren't working fine (FN + F5-7 and F10 and F12 are not supported)

only Fn+ Num or Einfg or Entf are working

---

### Post by krang on 2008-03-31
benste: I think, you're right. xrandr seems not working for you... :( Maybe with the new Ubuntu and the new Xorg... 8.04 (beta) fixed my problem with this ... ati driver for my (laugh, please!) radeon 9200 mobile

interestingly the FN-Keys make my linux change the brightness just as they did with windows but the other assigned "FN-KEYS" like pause or switching display do not give any command =)

okok, I have to use the super-key instead then :)

---

