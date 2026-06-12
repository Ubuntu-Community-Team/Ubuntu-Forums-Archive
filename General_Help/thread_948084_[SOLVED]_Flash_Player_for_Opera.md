---
title: "[SOLVED] Flash Player for Opera"
date: 2008-10-14
forum: General Help
---

### Post by GrumpyGrenade on 2008-10-14
Hello,
I'm having a hard time installing flashplayer on opera 9.6 in hardy. Could anyone shed some light on my situtation? :confused:

Thanks

---

### Post by Altay_H on 2008-10-14
Try going to:
Applications > Accessories > Terminal

and entering the following:
```
sudo apt-get install flashplugin-nonfree
```


Alternatively you could use System > Administration > Synaptic Package Manager and search for flashplugin-nonfree.


Note:
If that doesn't work, open Opera, go to Tools > Preferences > Advanced > Downloads, find swf in the list, and click Edit. Then check to make sure that the "Use plug-in" option is selected and that the plug-in you're using is "Shockwave Flash -/usr/lib/flashplugin-nonfree/libflashplayer.so.

---

### Post by GrumpyGrenade on 2008-10-14
That really helped. Thank you very much! :)

---

### Post by rony474 on 2008-10-15
thank you very much i had the same problem ... quick fix ...
keep the good work :)

---

### Post by Tomatz on 2008-10-15
Or just do this....

Open a terminal then type:


```
sudo cp ~/.mozilla/plugins/libflashplayer.so /usr/lib/opera/plugins
```


Restart Opera

Done ;)

---

### Post by Tomatz on 2008-10-15
Also, if you cant get totem to work in Opera. The vlc plugin works quite nice.

Just **download the attachment below** (and extract).

Then

Open a terminal and type:

```
sudo apt-get install vlc
```

Then type

```
sudo nautilus
```

Then browse to ***/usr/lib/opera/plugins*** and paste the **libvlcplugin.so** file there.

Restart opera.

The only drawback is that you have no control buttons also you may need to disable **Totem** in the opera plugins settings.

---

### Post by anadeau on 2008-10-18
I've been trying to figure this out for most of the day now (Flashplayer on Opera). I've tried all the options above (and many others) and it's still not picking up the Plugin for some reason... I am using Ubuntu 7.10 and Opera 9.60... any other suggestions? Thank you.

-- Adrian

---

### Post by anadeau on 2008-10-18
> **Altay_H said:**
> Try going to:
Applications > Accessories > Terminal

and entering the following:
```
sudo apt-get install flashplugin-nonfree
```


Alternatively you could use System > Administration > Synaptic Package Manager and search for flashplugin-nonfree.


Note:
If that doesn't work, open Opera, go to Tools > Preferences > Advanced > Downloads, find swf in the list, and click Edit. Then check to make sure that the "Use plug-in" option is selected and that the plug-in you're using is "Shockwave Flash -/usr/lib/flashplugin-nonfree/libflashplayer.so.

I tried both of these. When I look in the /usr/lib/flashplugin-nonfree/ folder I don't see any files (after uninstalling and reinstalling it also).

Thanks.

---

### Post by Tomatz on 2008-10-20
Try this (after installing flashplugin-nonfree):


> sudo cp ~/.mozilla/plugins/libflashplayer.so /usr/lib/opera/plugins

---

### Post by Chobicus on 2009-08-02
I tried all of the above.
I have installed libflashplayer.so. It's in usr/lib/flashplugin-installer.
I copied it to usr/lib/opera/plugins and set Tools > Preferences > Advanced > Downloads to use this plugin for swf files.

What did I do wrong?

---

### Post by Colonel Kilkenny on 2009-08-03
> **Chobicus said:**
> I tried all of the above.
I have installed libflashplayer.so. It's in usr/lib/flashplugin-installer.
I copied it to usr/lib/opera/plugins and set Tools > Preferences > Advanced > Downloads to use this plugin for swf files.

What did I do wrong?

I'm not sure why would you need to go to Tools -> Preferences -> Advanced -> Downloads ...
The right place would be Tools -> Preferences -> Advanced -> Content -> Plugin options. And make sure that Opera searches for that *.so file. (It's usually good idea to make sure that it finds only one flashplugin...)

---

### Post by caeroe on 2009-08-04
> **Colonel Kilkenny said:**
> I'm not sure why would you need to go to Tools -> Preferences -> Advanced -> Downloads ...
The right place would be Tools -> Preferences -> Advanced -> Content -> Plugin options. And make sure that Opera searches for that *.so file. (It's usually good idea to make sure that it finds only one flashplugin...)

Doesn't work here.  Opera sees Flash, and in one path.  However only the audio portion loads, where the video would be is just an empty space.

---

### Post by -=hazard=- on 2009-08-04
The problem seems to be with the last version of opera.

---

