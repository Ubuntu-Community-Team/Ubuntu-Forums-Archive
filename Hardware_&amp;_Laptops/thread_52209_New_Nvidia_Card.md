---
title: "New Nvidia Card"
date: 2005-07-26
forum: Hardware &amp; Laptops
---

### Post by badboyz107 on 2005-07-26
[FONT=Trebuchet MS]Hey all hopefully I will be able to get a handle on what is going on here....I had Ubunto installed on an old IBM with on mobo graphics etc, then I did some tinkering and installed a GF4 MX4000 PCI card.  Restarted the puter and after all the start up it goes to black screen....No GUI or anything

I removed the card put the video back on the mobo video and works just fine!  What do I need to do while I have the new card in so that it will work??

Keep in mind that im COMPLETELY new to Linux so dont really know what to do or how....can someone PLEASE help me!!![/FONT][/SIZE]

---

### Post by strikeforce on 2005-07-27
[QUOTE=badboyz107][FONT=Trebuchet MS]Hey all hopefully I will be able to get a handle on what is going on here....I had Ubunto installed on an old IBM with on mobo graphics etc, then I did some tinkering and installed a GF4 MX4000 PCI card.  Restarted the puter and after all the start up it goes to black screen....No GUI or anything

I removed the card put the video back on the mobo video and works just fine!  What do I need to do while I have the new card in so that it will work??

Keep in mind that im COMPLETELY new to Linux so dont really know what to do or how....can someone PLEASE help me!!![/FONT][/SIZE][/QUOTE]

This will help you get started,

[http://ubuntuguide.org/](http://ubuntuguide.org/)

you might have to edit your xorg.conf file by doing a failsafe boot and editing that way.  I think the reason is the driver its trying to load is your old mobo video card.

---

### Post by codejunkie on 2005-07-27
[QUOTE=badboyz107][FONT=Trebuchet MS]Hey all hopefully I will be able to get a handle on what is going on here....I had Ubunto installed on an old IBM with on mobo graphics etc, then I did some tinkering and installed a GF4 MX4000 PCI card.  Restarted the puter and after all the start up it goes to black screen....No GUI or anything

I removed the card put the video back on the mobo video and works just fine!  What do I need to do while I have the new card in so that it will work??

Keep in mind that im COMPLETELY new to Linux so dont really know what to do or how....can someone PLEASE help me!!![/FONT][/SIZE][/QUOTE]

go into the bios make sure that the onboard video card is completly disabled if it's not you will still have the same problems even if you change the video driver when you have disabled the onboard video then edit your /etc/X11/xorg.conf file with this 
```
sudo nano /etc/X11/xorg.conf
``` 
find the section i've marked in blue
```

Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
	[COLOR=Blue]Driver		"nvidia"[/COLOR]
	BusID		"PCI:1:0:0"

```
example: where mine says "nvidia" you would replace what yours has with either "nv" or "vesa" save the file restart the xserver with 
```
sudo /etc/init.d/gdm restart
``` 
now when the gui starts you need to install the nvidia driver to have opengl support  you do that with 
```
sudo apt-get install nvidia-glx nvidia-settings
``` then enable the nvidia driver with ```
nvidia-glx-config enable
``` after you've installed the nvidia driver you should restart the computer.

---

### Post by badboyz107 on 2005-07-27
[QUOTE=codejunkie]go into the bios make sure that the onboard video card is completly disabled if it's not you will still have the same problems even if you change the video driver when you have disabled the onboard video then edit your /etc/X11/xorg.conf file with this 
```
sudo nano  /etc/X11/xorg.conf
``` 
find the section i've marked in blue
```

Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
	[COLOR=Blue]Driver		"nvidia"[/COLOR]
	BusID		"PCI:1:0:0"

```
example: where mine says "nvidia" you would replace what yours has with either "nv" or "vesa" save the file restart the xserver with 
```
sudo /etc/init.d/gdm restart
``` 
now when the gui starts you need to install the nvidia driver to have opengl support  you do that with 
```
sudo apt-get install nvidia-glx nvidia-settings
``` then enable the nvidia driver with ```
nvidia-glx-config enable
``` after you've installed the nvidia driver you should restart the computer.[/QUOTE]
 Hey wow see thats why I like this board...quick replies to stupid ass questions.....I'm setting this one up for shits and giggles, oh and some headaches....I'll let you know how it goes...

---

### Post by badboyz107 on 2005-07-27
[QUOTE=badboyz107]Hey wow see thats why I like this board...quick replies to stupid ass questions.....I'm setting this one up for shits and giggles, oh and some headaches....I'll let you know how it goes...[/QUOTE]
 okey dokey so I did the sudo nano command and it takes me to a blank absolutely nothing editor....cant find anything except blank screens....????.....Am I to stupid to be trying to use this OS?

---

### Post by strikeforce on 2005-07-27
[QUOTE=badboyz107]okey dokey so I did the sudo nano command and it takes me to a blank absolutely nothing editor....cant find anything except blank screens....????.....Am I to stupid to be trying to use this OS?[/QUOTE]

No it just seems like the current nvidia drivers are broken? Although I'm not so sure.  I still think something is stuffing up.

You following the nvidia guide from the ubuntuguide.org because thats exactly the same as the previous post on the howto.

---

### Post by badboyz107 on 2005-07-27
yeah I tried that how to before even posting on this part....
sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

doesnt work at all, well the first sudo apt-get did but none of the others...
I had even just reformatted and done a clean install before even looking around on here cause I always fingure thats the "easy" way to fix it...lol

what would the sudo nano screen look like when it works right?

---

### Post by codejunkie on 2005-07-27
[QUOTE=badboyz107]okey dokey so I did the sudo nano command and it takes me to a blank absolutely nothing editor....cant find anything except blank screens....????.....Am I to stupid to be trying to use this OS?[/QUOTE]
no that was a typo on my part sorry, if you copied and pasted the code i added one to many spaces in the command try it again it's fixed and should work.
if it doesn't again try 
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by badboyz107 on 2005-07-27
[QUOTE=codejunkie]no that was a typo on my part sorry, if you copied and pasted the code i added one to many spaces in the command try it again it's fixed and should work.
if it doesn't again try 
```
sudo dpkg-reconfigure xserver-xorg
```[/QUOTE]
 HELL!!!

Okay so I followed the guide directions exactly with the whole
sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

When I got to the last line "sudo gedit" etc it tossed this back at me
(gedit: 5516)  Gtk-WARNING **:  cannot open display

So not knowing what the hell that meant I went ahead and rebooted hoping that all would work perfectly.....of course I was very wrong

I ended up getting some blue screen saying that my xserver wasnt configured correctly or was corrupt.....and that I should fix this....of course I dont know how....gah

Ive become retarted by Window$ products and cant finger anything else out now!!!!

---

### Post by badboyz107 on 2005-07-27
Okay once again 

AM I TO STUPID TO USE THIS???

I did get the sudo nano /etc/X11/xorg.conf to work and it showed the stuff you said it would
however in the Section you showed me mine says this

Identifier   Intel Corporation 82810E CD-133 CGC Chipset Graphics Controller
Driver        Nvidia

I'm guessing that the two seperate things cant be together like that but how do I change the identifier so that it shows the gf4 mx4000 that I have in there now???

---

### Post by Omnios on 2005-07-27
Nano is like a terminal/command line type text editor, Gedit is a graphical text edit which you can not use in command line as far as I know though you can use in in gnome from terminal. I had a similar problem before where it would not properly apply the config sudo nvidia-glx-config enable part so I rebooted started in recovery and aplyed the config enable which got if working. 

 Also not shure if things changed but when 5.04 first came to use (one sec have to find this in my ever growing notebook) "Sudo dpkg-reconfigure xserver-xorg " which is the graphical x setup. You used to have to edit  " sudo nano /etc/X11/xorg.conf " with the following option in device some please correct this and I can barely make it out in my notes. show Driver "nvidia" which puts the nvidia driver into the "Sudo dpkg-reconfigure xserver-xorg " list of drivers. 

 Getting out Xserver and using " sudo nvidia-glx-config enable" should fix it unless there is something else (more serios wrong)

 Oh ya the gedit setting part is suppoed to be done after you log into gnome I believe. Least thats the way I did it.

 Also the " sudo nvidia-glx-config enable" sets up your xorg.conf file for the nividia driver which is probably your culperate if your getting the the blue box crash.

 ALso there are many possible solutions to the same problem which makes it so difficult

 ALso your supposed to use sudo apt-get update to update apt-get package list I think I had a problem with this way back then to. 
WHen I had this problem I went over the list of apt-get stuff and found most of it was already there as apt-get stated it was already local. But when I got to some of the stuff it was not there and was finaly applied. 

 Hope this help explaining some stuff.

---

### Post by badboyz107 on 2005-07-27
WAAAHOOOOOOO

I fixed it on my own so maybe Im not as stupid as I thought.....well dont ask my friends anyway.....

It was the PCI setting...set to default I guess of 0.1.0 and was really supposed to be 1.5.0 and now Im in the GUI....thanks for all the help, Im sure I'll be back on here soon enough!!

---

### Post by badboyz107 on 2005-07-27
[QUOTE=Omnios]Nano is like a terminal/command line type text editor, Gedit is a graphical text edit which you can not use in command line as far as I know though you can use in in gnome from terminal. I had a similar problem before where it would not properly apply the config sudo nvidia-glx-config enable part so I rebooted started in recovery and aplyed the config enable which got if working. 

 Also not shure if things changed but when 5.04 first came to use (one sec have to find this in my ever growing notebook) "Sudo dpkg-reconfigure xserver-xorg " which is the graphical x setup. You used to have to edit  " sudo nano /etc/X11/xorg.conf " with the following option in device some please correct this and I can barely make it out in my notes. show Driver "nvidia" which puts the nvidia driver into the "Sudo dpkg-reconfigure xserver-xorg " list of drivers. 

 Getting out Xserver and using " sudo nvidia-glx-config enable" should fix it unless there is something else (more serios wrong)

 Oh ya the gedit setting part is suppoed to be done after you log into gnome I believe. Least thats the way I did it.

 Also the " sudo nvidia-glx-config enable" sets up your xorg.conf file for the nividia driver which is probably your culperate if your getting the the blue box crash.

 ALso there are many possible solutions to the same problem which makes it so difficult

 ALso your supposed to use sudo apt-get update to update apt-get package list I think I had a problem with this way back then to. 
WHen I had this problem I went over the list of apt-get stuff and found most of it was already there as apt-get stated it was already local. But when I got to some of the stuff it was not there and was finaly applied. 

 Hope this help explaining some stuff.[/QUOTE]
 Hey thanks for filling in some of my "huh what" questions there Omnios....

Now I just have to fix all that irritating mp3 bs and all that

Quick off post question....

do I need to run an AV program on this thang or not?  and if yes is there a free one somewere like avast for Window$?

---

### Post by varunus on 2005-07-27
You shouldn't need to run an antivirus program in Linux.  If you're paranoid or want to run one anyway, there's a howto on how to set up F-prot in the "Hoary Tips and Tricks" section of the forum.  (Check the "Index of HOWTOS" post if you can't find it immediately).

ClamAV is another antivirus program, command-line only though, so you may want to go with F-prot.  (Clam stays nice and out of the way though.)  Instructions here: [http://www.ubuntuguide.org/#antivirusserver](http://www.ubuntuguide.org/#antivirusserver)

EDIT:  Oh, and to fix the mp3 stuff, just head over to [http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs) and follow the instructions.  Make sure to enable the extra repositories first as it says on that site too, though.

---

### Post by badboyz107 on 2005-08-04
HEY anyone that see's this thread....

Okay so I got the NV card to work but here is my newest problem

EVERY time I reboot the computer the display resolution resets to 640-480 and has NO other options....I have to run xserver-xorg everytime I reboot to make it work

why does it do this to me and how do I resolve this issue????

---

### Post by Omnios on 2005-08-04
[QUOTE=badboyz107]HEY anyone that see's this thread....

Okay so I got the NV card to work but here is my newest problem

EVERY time I reboot the computer the display resolution resets to 640-480 and has NO other options....I have to run xserver-xorg everytime I reboot to make it work

why does it do this to me and how do I resolve this issue????[/QUOTE]

 That is strange it useually sets the max res in config does that happen in gnome, and have you tryed the res set in gnome system preferences. If you ran reconfigure you should also make shure its set to the nvidia driver. As mentioned earlier in reconfig you can check the reses by space to set them and then check your sudo nano /etc/X11/xorg.conf and possibly post it on the forum, I think it probably has something to do with the config file and will show up near the bottom with color depth and reses.

---

### Post by varunus on 2005-08-04
Can you post your /etc/X11/xorg.conf?  Especially the Screen section.  Also, make sure the driver is set to nvidia in the xorg.conf file under the Device section.

GNOME's resolution can sometimes default down to 640x680; after running a reconfigure of xorg, can you open up screen resolutions in GNOME and make sure its set to what you want?

---

### Post by badboyz107 on 2005-08-05
[QUOTE=varunus]Can you post your /etc/X11/xorg.conf?  Especially the Screen section.  Also, make sure the driver is set to nvidia in the xorg.conf file under the Device section.

GNOME's resolution can sometimes default down to 640x680; after running a reconfigure of xorg, can you open up screen resolutions in GNOME and make sure its set to what you want?[/QUOTE]
 Well I would post the xorg.conf file if I could remote to the machine right now....lol....I have actually set this puter up for my parents (55+) and that is not a kind thing to do to old people let me tell you.....

It seems as if this problem arises every time they shut it down.....when it does happen you cannot change it from the screen resolution as it show 640-480 only.....

I did try sudo nvidia-glx-config enable yesterday had them shut it down leave it for a few minutes then start it up and seemed to be okay.....

What would be the benifits to installing the linux drivers from the nvidia web site as opposed to the ones that are built in???

I will post the xorg.conf whenever they turn it on for me.....THANKS

---

### Post by badboyz107 on 2005-08-16
[QUOTE=badboyz107]Well I would post the xorg.conf file if I could remote to the machine right now....lol....I have actually set this puter up for my parents (55+) and that is not a kind thing to do to old people let me tell you.....

It seems as if this problem arises every time they shut it down.....when it does happen you cannot change it from the screen resolution as it show 640-480 only.....

I did try sudo nvidia-glx-config enable yesterday had them shut it down leave it for a few minutes then start it up and seemed to be okay.....

What would be the benifits to installing the linux drivers from the nvidia web site as opposed to the ones that are built in???

I will post the xorg.conf whenever they turn it on for me.....THANKS[/QUOTE]
 Holy Crap folks!!!

Okay here are my problems that CONTINUE with this computer!
#1  I DONT know how to copy and paste from the xorg.conf.....I know that seems stupid and              easy but there it is....someone tell me how to do this

#2  The xorg.conf doesnt seem to show anything out of the ordinary that I can see regardless of what the current resolution on the screen is....everything looks exactly the same

#3  The really odd thing here is that it will only offer 640-480 and I didnt even enable that particular resolution when I did the config

#4   If you start it up and the resolution is FUBAR, they have discovered that if you restart it that the resolution changes back to 1024-768 (which is what they want!!!)

HELP!

---

