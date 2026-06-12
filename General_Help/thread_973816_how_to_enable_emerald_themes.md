---
title: "how to enable emerald themes??"
date: 2008-11-07
forum: General Help
---

### Post by poision_heart on 2008-11-07
hi 
i am using ubuntu 8.04.1 i recently downloaded nice theme known as google-chome for metacity n emerald.

when i tried to install this theme in metacity it shows error in file cant install..other hand when i tried to install it in emerald theme manager it installed but i dont know how to activate it..
can anyone help me to activate it in emerald or in metacity??

pls guide me

---

### Post by slinkey1981 on 2008-11-07
As I recall, most Emerald themes end in .emerald

With Emerald, are you using the Import button?

I know it sounds silly, but I had problems with themes when using drag & drop....

Also, if it does import it, but you aren't seeing it, try ALT-F2 and entering

```
compiz --replace&
```
If that works and the theme isn't loading, make sure that Compiz (I assume you are running compiz) Is running Emerald by looking at the "Window Decoration" plugin and specifically the "command"  line.

It should say: ```
emerald --replace
```

Alternately, could you post a link to the file you are trying to use? Then I would be able to tell you exactly how to use the theme in question.

---

### Post by poision_heart on 2008-11-07
hi slinkey

yeah extactly i m using that "import" button.yeah i can see my theme there but i m not getting how to activate it..i mean i would like to use emerald themes instead of metacty themes..here i am attaching theme file pls have a look..

i am trying with ur commands now..

reply me

---

### Post by slinkey1981 on 2008-11-07
Ok, I don't know exactly why they did it like this.

First, open the Google_Gnome_by_Macwanderer.gz 
In that is GoogleGnomePack.tar
In that you will have the following:

Google_Chrome-GTK.tar.gz    -   which you add through System>Preferences>Appearance>Theme

Google_Gnome.emerald  -  which you add through Emerald

GoogleMenu.png  -  I don't know about these two.....
GoogleMenuLarge.png

As soon as the Metacity and Emerald themes are installed (if it's correct) it should either switch, or ask you if you want to change to the newly installed theme.

---

### Post by poision_heart on 2008-11-07
hi

metacity theme showing error while installing but it installed in emerald but its not activation that theme..thats problem i am facing how to activate it from emerald??

---

### Post by eternalnewbee on 2008-11-07
Just click on the theme.

---

### Post by stinedvd on 2008-11-08
I've got the same problem.  I click on the Theme, but it doesn't apply/change the current theme.

Ubuntu 8.10
Emerald Theme Manager 0.7.2

---

### Post by fickenbaisage on 2008-11-08
> **stinedvd said:**
> I've got the same problem.  I click on the Theme, but it doesn't apply/change the current theme.

Ubuntu 8.10
Emerald Theme Manager 0.7.2

Press ALT+F2 and type "emerald --replace" w/o the quotes.

---

### Post by slinkey1981 on 2008-11-08
> **fickenbaisage said:**
> Press ALT+F2 and type "emerald --replace" w/o the quotes.

Exactly, and if you are using Compiz, you can switch which Window Decorator it uses by using the Window Decorator.

**Compiz 0.7.4**
```
System>Preferences>Advanced Desktop Effects Settings
```

**Compiz 0.7.6**
```
System>Preferences>CompizConfig Settings Manager
```

Click on the "Effects" button on the left side, it will change the view on the right.
You want the plugin marked "Window Decoration"

Once selected, you need to check (and edit) the 6th option down on the right to say;
```
emerald --replace
``` (see Screenshot.)

This way, if you have Compiz and Emerald installed, with Compiz set to autostart, it will automatically change your borders to that of the Emerald theme that you have chosen.

---

### Post by edge_nabby on 2008-11-08
I'm sure that this is the answer of your question. Install fusion-icon. It provides you to choose gtk or emerald.

---

### Post by stinger30au on 2008-11-08
i have the same issue, i have fusion icon installed and emerald and nothing sticks


i think its cos im using the beta driver for my nvidia card and nvidia have not released final driver yet

my video in wine is screwed up as well since i installed beta driver too

---

### Post by poision_heart on 2008-11-10
thanks buddy i ll try this now n let u know..thanks again

---

### Post by Ocelaris on 2008-11-12
> **fickenbaisage said:**
> Press ALT+F2 and type "emerald --replace" w/o the quotes.

Thanks, that worked for me... not sure why emerald-themes won't install anymore, just have the one I downloaded.

---

### Post by //source\\ on 2008-11-21
I'm brand new and just installed ubuntu 8.10 with wubi. Everthing works fine but my emerald themes. I tired both "emerald --replace and compiz --replace" and get this....

cav@ubuntu:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Starting gtk-window-decorator

I get that code using "compiz --replace" when I use "emerald --replace" it only works on the border of the window till i close the terminal then it deletes the border around my windows.

here is my xorg.conf

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "Default Screen" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection

I have an ATI 2500 HD PRO video card. I been reading and reading through all the forums and cant seem to completely get it to work 100% Some of compiz works... like the window wobble... the cube... but themes and drawing fire and such does not work.I have all the packages from Synaptic installed that are necessary to run emerald and compiz...at least i think i do. My compiz settings manager is up and running...but not everything works on it. I have also installed... "/ati-driver-installer-8.41.7-x86.x86_64.run" but that didnt seem to work either. I do have the ATI/AMD proprietary FGLRX graphics driver activated.... can anyone help a fellow NOOBUNTU guy out? lol...

---

### Post by eternalnewbee on 2008-11-21
> I'm brand new and just installed ubuntu 8.10 with wubi. Everthing works fine but my emerald themes. I tired both "emerald --replace and compiz --replace" and get this....
Have you tried enabling visual effects?
Go to: **Main Menu > System > Preferences > Appearance > Visual Effects**, and click **Normal** or **Extra**, and see what happens.

---

### Post by edwardtilbury on 2009-08-28
Thanks.. That emerald --replace thing works great when I start up... That should be a default when we install emerald... Good thing you're on the forum, there's no way that I'd figure that out.

Old school dell XPS M140 and I have compiz and emerald running on this beast... I love it.

---

