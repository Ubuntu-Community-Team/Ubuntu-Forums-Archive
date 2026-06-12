---
title: "No videos with opera 9.64"
date: 2009-07-23
forum: Installation &amp; Upgrades
---

### Post by harsha10 on 2009-07-23
Hi all !! 
i just now installed opera from the opera site and installed flashplugin nonfree .. to enable flash in web browsers ..in 9.04 ..
youtube videos are not working in opera but working with others i.e firefox and konqueror :( and i am much acquainted with opera rather that firefox .. 

please help me ( a newbie to ubuntu ) .. and tell me how to enable flash with opera in xubuntu 9.04..

---

### Post by harsha10 on 2009-07-24
hey guys .. is it the problem with opera or something else...
Please help me out to sort this problem..

waiting for reply ..

---

### Post by captaincrook on 2009-07-25
I had problems like this and its with the wrapper imo. It works tons better if you copy over the plugin from wherever its installed.

I'm not aware where that package installs to, but it should be somewhere like in /usr/lib/flashplugin-nonfree/. If I am correct (you can check yourself by looking there in Thunar) you want to do this:

Open up a terminal, type this in

```
sudo cp /usr/lib/flashplugin-nonfree/libflashplayer.so /usr/lib/opera/plugins
```

Then open up Opera. Go to Tools/Preferences/Advanced/Content/Plugin Options. IF you don't see "/usr/lib/opera/plugins" at the bottom/ click on Change Path. Add the folder /usr/lib/opera/plugins. If its added/You just added it, make sure its up top, AOVE any other directory, i.e. the first. Make sure the checkbox for Use is ticked, and click ok. Click on "Find New" and it should pick up your opera plugins folder. Restart Opera and you should be good to go.

---

### Post by harsha10 on 2009-07-31
Hey captain cook !! Thanks for ur reply .. 

I have done the same thing i.e i copied the libflashplayer.so in plugins directory and checked whether the plugins dir was shown in the content/plugins option ...

it shows the following the following :- 
1. mozilla dir 
2. firefox dir 
3. opera dir  ( dir -> plugins directory )

For the plugin, i have the following path 
```

/usr/lib/opera/plugins:/usr/lib/mozilla/plugins:/usr/lib/firefox/plugins

```

and more over the opera/plugins dir is on top of the above list ..

but still i get a white screen when i view youtube videos . :(

please help me .. its all working in firefox and chromium .. but not in opera .. :(

---

### Post by captaincrook on 2009-08-02
Have you tried running it via terminal to see any outputs it might give?

---

### Post by vinutux on 2009-08-02
Open opera

tools>preferences>Advanced>Content>Plug-in options>Change path and add paths of mozill/firefox lib folders contained **libflash.so**

---

### Post by abautu on 2009-08-06
I'm having the same problem in Ubuntu Jaunty 32bit. However, last weekend I installed Jaunty amd64 and flash worked ok. Two days later, I had to revert to Ubuntu Jaunty 32bit (for memory reasons), and Flash in Opera stopped working again.

In terminal, I get this message "Not GTK2 toolkit (got 0)", and I read somewhere that Flash 10 requires GTK2 containers (which are used in Opera 10, but not in Opera 9).

---

