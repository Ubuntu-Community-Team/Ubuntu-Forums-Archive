---
title: "Startup-Manager with grub2 has no options"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by lindsay7 on 2009-06-17
I installed grub2 and am trying to change the background color of the start menue. I have "Startup-Manager" installed, but now there are no options listed to change much after the installation of grub2.

Can anyone tell me how to change the start menu. Here is the screen shot of the Statup-Manager menu.  IS the change to Startup- Manger just because of grub2 or is there a way to get back the features that the original one had?



[ATTACH]117998[/ATTACH]

---

### Post by lindsay7 on 2009-06-18
Well, I found out how to change the screen to a picture but not change the color, which is fine with me. I just did not like the similarity to the BSOD.

Here is the info and link, Note I used gedit and not nano to edit the file.

[http://blogs.koolwal.net/2008/12/16/how-to-grub2-and-grub-pc-installing-splash-images/](http://blogs.koolwal.net/2008/12/16/how-to-grub2-and-grub-pc-installing-splash-images/)

---

### Post by raymondh on 2009-06-18
> **lindsay7 said:**
> Well, I found out how to change the screen to a picture but not change the color, which is fine with me. I just did not like the similarity to the BSOD.

Here is the info and link, Note I used gedit and not nano to edit the file.

[http://blogs.koolwal.net/2008/12/16/how-to-grub2-and-grub-pc-installing-splash-images/](http://blogs.koolwal.net/2008/12/16/how-to-grub2-and-grub-pc-installing-splash-images/)


Thanks Lindsay ...

---

### Post by shantiq on 2010-11-02
cool stuff to change the background image on startup

this is the info from the link

[COLOR=#000000][FONT=Times New Roman][LEFT]```


sudo apt-get update
sudo apt-get install grub2-splashimages
```[FONT=Trebuchet MS]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]The new GRUB2 splash images are installed at:


[/COLOR][/FONT]```
[FONT=Trebuchet MS] # ls /usr/share/images/grub/[/FONT]
```[FONT=Trebuchet MS]
[COLOR=#000000]Output:[/COLOR]
[/FONT]```
050817-N-3488C-028.tga                  Glasses_800_edit.tga
2006-02-15_Piping.tga                   Hortensia-1.tga
Aesculus_hippocastanum_fruit.tga        Lake_mapourika_NZ.tga
Apollo_17_The_Last_Moon_Shot_Edit1.tga  Moraine_Lake_17092005.tga
B-1B_over_the_pacific_ocean.tga         Plasma-lamp.tga
BonsaiTridentMaple.tga                  Sparkler.tga
Flower_jtca001.tga                      TulipStair_QueensHouse_Greenwich.tga
Fly-Angel.tga                           Windbuchencom.tga#
```[FONT=Trebuchet MS][COLOR=#000000]


**and** of course one might want to add one's own images to the list   format is  640X480 and tga

[COLOR=#008000][U][B]Change the GRUB2 splash image

[/B][/U][/COLOR][/COLOR] [COLOR=#000000]Now we will see how we can change the default GRUB2 splash image. First select the image file that you want to install from the following locations:[/COLOR]
[/FONT]```

/usr/share/images/desktop-base/
/usr/share/images/grub/
```[FONT=Trebuchet MS][COLOR=#000000]

For this example, I have selected &#8220;Plasma-lamp.tga&#8221; from /usr/share/images/grub/.
Now edit the file following file:[/COLOR]
[COLOR=#000000]
[/COLOR][/FONT]```
[FONT=Trebuchet MS] # nano /etc/grub.d/05_debian_theme[/FONT]
```[FONT=Trebuchet MS]
[COLOR=#000000]and change the following line from:[/COLOR]
[/FONT]```
[FONT=Trebuchet MS] for i in {/boot/grub,/usr/share/images/desktop-base}/moreblue-orbit-grub.{png,tga}[/FONT]
```[FONT=Trebuchet MS][COLOR=#000000]
**to**
[/COLOR][/FONT]```
for i in {/boot/grub,/usr/share/images/desktop-base,/usr/share/images/grub}/Plasma-lamp.{png,tga}
```  [FONT=Trebuchet MS][COLOR=#000000]and save the file.

well on maverick it looks like this:


[/COLOR][/FONT]```
# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  . ${f}
else
 [COLOR=Red] WALLPAPER="/usr/share/images/grub/screen44.tga[/COLOR]"
  COLOR_NORMAL="black/black"
  COLOR_HIGHLIGHT="magenta/black"
```    but i guess basically the same idea



Now you need to regenerate the grub.cfg file by giving the following command:
[/COLOR][/FONT]```
[FONT=Trebuchet MS] sudo update-grub[/FONT]
```[FONT=Trebuchet MS][COLOR=#000000]
[/COLOR][/FONT]```
Updating /boot/grub/grub.cfg ...
Found Debian background: Plasma-lamp.tga
Found linux image: /boot/vmlinuz-2.6.26-rt1-rt
Found initrd image: /boot/initrd.img-2.6.26-rt1-rt
Found linux image: /boot/vmlinuz-2.6.26-1-686
Found initrd image: /boot/initrd.img-2.6.26-1-686
Found linux image: /boot/vmlinuz-2.6.25-2-686
Found initrd image: /boot/initrd.img-2.6.25-2-686
done
#
```[FONT=Trebuchet MS]
[COLOR=#000000][COLOR=#008000]_** Further customization**_[/COLOR]
You can further customize the text color and all by editing the file:
[/COLOR][/FONT]> [COLOR=#000000] /etc/grub.d/05_debian_theme[/COLOR][FONT=Trebuchet MS]
[COLOR=#000000]That&#8217;s it. We are done here.[/COLOR]
[/FONT][/LEFT]
[/FONT][/COLOR]

---

