---
title: "Nvidia Drivers 8756 failed"
date: 2006-04-23
forum: Hardware &amp; Laptops
---

### Post by Unoone on 2006-04-23
Ok. I'm a new Linux/ubuntu Breezy user, actually an off and on user. I like to use Linux but I don't have all the time in the world to mess with it. 

I installed the latest Nvidia 8756 Drivers. Oh yeah I failed. I saw tseliot's tips and followed them. They worked then after a another reboot they failed.

All I want to know now is how to remove the 8756 drivers and go back to a generic nv driver. When I can boot back to Gnome I may try tseliot's 8756 scripts. 

I only installed the 8756 driver due to the default glx drivers dying after a bout with the Automatix. The official Nvidia drivers worked the best when I could boot up to them.

Thanks for your help!

---

### Post by woedend on 2006-04-23
to use the nv driver, simple type
If you are in gnome, use  sudo gedit /etc/X11/xorg.conf

If you are stuck in command line, which I just now though of, use vi instead of gedit.
sudo vi /etc/X11/xorg.conf
push down arrow to get to the section below, push insert key to be able to edit the line, once it looks right, push escape, then type  :wq     and push enter.


change your device from  "nvidia"  to "nv", so if you had this ```
Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"

```

make it say this

```

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nv"
	BusID		"PCI:2:0:0"

```

Only change the driver line, not the others!  
to uninstall, if you download the driver from the nvidia website(the .run file), simply go to terminal and run sudo NameOfNvidiaDriver.run --uninstall

---

### Post by Unoone on 2006-04-23
Thanks for those tips. What I did to get things back right was to use the command-
"sudo dpkg-reconfigure xserver-xorg" . 

Then I set driver to vesa. This forum is great. I did a quick search and I was back in Gnome.

Now on this computer I started out with Hoary then I moved to Mandriva. I didn't like Mandriva on this PC so I decided to move to Breezy. 

The PC is my Linux test box. It's a P3 1gig with and old Nvidia Geforce MX 400 card. When I had Hoary running on this machine the Nvidia official cards installed with out a hitch. And in Mandriva the Nvidia driver install was perfect. Now with Breezy the Nvidia Universe drivers clash with Automatix. I was using Automatix to get a Opera, etc, etc. really easy. I figure that "todays" hot Linux Distros should install all the basics with ease. 

In all of my Linux installations on this pc I have never had trouble with my Nvidia drivers. I even set up Gentoo on this box. I know that was a trip. But it got Nvidia drivers working with everything else. Too much of a hassle for me to deal with though. 

Does anyone know of a way to get a Nvidia driver working with opengl support on my type of setup in Breezy? 

I used tseliot's tips and installed the kernels and all on the 8756 setup. I saw more of the insides of a user friendly Linux Distro than I ever did for a basic driver setup.
I learned a lot and some things I rather not mention with the kids in the room. 

I don't want to go there again for a Nvidia driver setup. I'll save that for compiling Gimp, setting up a internet server, etc, etc.

Thanks for your help.

---

### Post by Unoone on 2006-04-23
[QUOTE=woedend]to use the nv driver, simple type
If you are in gnome, use  sudo gedit /etc/X11/xorg.conf

If you are stuck in command line, which I just now though of, use vi instead of gedit.
sudo vi /etc/X11/xorg.conf
push down arrow to get to the section below, push insert key to be able to edit the line, once it looks right, push escape, then type  :wq     and push enter.


......[/QUOTE]

I did - "sudo gedit /etc/X11/xorg.conf" and the file is empty. I reinstalled the nvidia drivers from Univers. Another thing, during the official Nvidia driver install phase there was a message like- "modules not found" and "modules not installed". Of course I can't see this during the Synaptic Nvidia driver setup.  My xorg.conf file was empty in Mandriva. I never checked it in Hoary.

Ah ha, it's case sense- /etc/"X11"/xorg.conf. Now it shows me stuff.

And it still the NV vesa driver even though installed the Nvidia-glx Universe driver. I wonder why that's not showing up in xorg.conf. It's like it didn't even install after all.

---

### Post by Unoone on 2006-04-23
I'm looking through Synaptic and thinking and looking. I right clicked on the properties of the installed nvidia-glx. It shows a Conflicts: nvidia-glx-src and Replaces: nvidia-glx-src. Now I found this by accident. What does this mean? Could it be the problem that stops me from getting my nvidia driver to work properly?

---

### Post by Unoone on 2006-04-23
Problem solved for now thanks to the Ubuntu forum. Thanks for your tips woedend. I fixed the problem using-

```
sudo apt-get install nvidia-glx
```    -even though it was already installed.

and

```
sudo nvidia-glx-config enable
```


:cool: :) 

I'll hold off on the Nvidia 8756 drivers for now.

Ubuntu is great folks I just had to make it more fun to use and paid for it. It's all good for now until the next time.;)

---

