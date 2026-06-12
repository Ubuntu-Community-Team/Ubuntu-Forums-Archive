---
title: "Mozilla java plugin"
date: 2005-11-03
forum: General Help
---

### Post by allroz on 2005-11-03
I have been trying forever to get this to work, and it just won't. I've installed blackdown java from synaptic, and i know that it works. I am running limewire to verify that it works. Im running a 64 bit. I have downloaded all the blackdown java's from synaptic. To my knowledge they should work with viewing java. I need to be able to see the images on [www.bmbw.com](www.bmbw.com) , and i belive that its java. Can someone please help me to get it so i can see them? Is there something that im missing? Im still a bit of a noob here, but im learning. Thanks.

---

### Post by allroz on 2005-11-03
No one knows???

---

### Post by zed007 on 2005-11-03
FYI.
Just checked out the site's page info & it's using the flash plugin not java. Sorry to be the bearer of bad news like that.:(  However, you could always try the gplflash which you can find using apt/synaptic. I've just found it to not be very effective. At least in my experience, I've yet to come across a site in which it would work. In any case, it's worth a shot at the least.

Craig

---

### Post by allroz on 2005-11-03
Ahhhhhh. Thanks. Didn't even realize that.

---

### Post by gravediggers on 2005-11-04
Not sure if deserves a new thread, and it's really along the same lines as this one, so I'll put it here. How do I install jre and flash plugins for Firefox. eg, for the java plugin, do I just download the bin file from Sun, and if so, where do i put it? Or do I have to install it as a package using apt, and where from and how? can it be done either way, and if so, is one better than the other?

---

### Post by MakubeX on 2005-11-04
[QUOTE=gravediggers]Not sure if deserves a new thread, and it's really along the same lines as this one, so I'll put it here. How do I install jre and flash plugins for Firefox. eg, for the java plugin, do I just download the bin file from Sun, and if so, where do i put it? Or do I have to install it as a package using apt, and where from and how? can it be done either way, and if so, is one better than the other?[/QUOTE]

From my experience (about 4-5 years), I download the JDK from [http://java.sun.com](http://java.sun.com) then place it in /usr/local and link the libjavaplugin from the JDK to the mozilla/firefox plugin folder.

---

### Post by allroz on 2005-11-04
You can also use synaptic manager to install it. Search for blackdown.

---

### Post by gravediggers on 2005-11-05
I was going to go with the first option for this, ie, download from Sun, but how do I link this to firefox? I also take the point that I can install the package, but this is where being new to this comes in - I don't know how to. Is there a good reference in the Wiki to doing this? I guess going with the package option means that you have more control of what is installed from a point of removing, updating, etc. Is this so?

---

### Post by Arktis on 2005-11-05
Here are links to complete howtos on [manual java installation](http://www.ubuntuforums.org/showthread.php?t=76754) or the much easier way, [creating a debian package](http://www.ubuntuforums.org/showthread.php?t=76735) for java that you can install with dpkg.

---

### Post by jonzep on 2005-11-06
here you'll find a guide to getting flash/java working in ubuntu (non foss versions)...

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by gravediggers on 2005-11-06
Thanx guys,

Will check all these methods out over the next day or two. Am tired and sunburnt now, so not a good time to start changing the system!

---

