---
title: "Need help: Automatically accept EULA with apt-get"
date: 2008-10-20
forum: General Help
---

### Post by ooshlablu on 2008-10-20
I need apt-get to automatically accept the licence agreement for Sun Java 6, which will be part of a script that generates amazon ec2 images. The rest of the script is all set, and this is the only thing that I need. Any help is appreciated

---

### Post by sethvath on 2008-10-20
sudo apt-get -y install sun-java6-bin

---

### Post by ooshlablu on 2008-10-20
that's what i though at first too, but -y is only for apt-get itself, for instance overwriting config files. I tried it, and it doesn't touch the EULA. thanks for the reply.

---

### Post by bodhi.zazen on 2008-10-20
When you install the EULA should come up. Scroll through it, hit the tab key, hit enter.

---

### Post by ooshlablu on 2008-10-20
is there some way that i could input the "tab" and "enter" keys in the bash script??? I need the eula to be accepted automatically with no user input.

---

### Post by sethvath on 2008-10-20
I was certain another java install script posted on this forum used a similar function with --yes 

Might have better luck doing a search here, I cant seem to find the exact one.

---

### Post by jamesstansell on 2008-10-20
For scripting bash you might look into expect or something similar. [http://www.kdab.net/~dfaure/scripts.html](http://www.kdab.net/~dfaure/scripts.html)

The sun-java6-* packages look for the presence of a file to indicate that the license has been accepted.  If you pre-create that file your install will probably succeed.

Or, you might consider the openjdk-6 packages.  On the server side they are _highly_ compatible with the sun-java6 packages.

Regards,

-james.

---

### Post by ooshlablu on 2008-10-20
thank you for the replies. As of yet, i still haven't found a solution, but please keep posting as I feel that there are many who will find this useful.

---

### Post by paskie on 2009-02-17
DEBIAN_FRONTEND=noninteractive apt-get install -y java5-sun-jre || :
 debconf 'echo SET shared/accepted-sun-dlj-v1-1 true; echo $(read) >&2'
 apt-get install -y java5-sun-jre

I so much hate dpkg for botching up this license stuff and taking 40 minutes of my life now...

---

### Post by raptor2552 on 2009-02-17
You can echo a tab in bash shells using:
```

echo $'\t'

\n = newline
\r = return
\t = tab
\v = vertical tab
\b = backspace
\a = "alert" (beep or flash)
-or- 
ASCII octal equivalent of 0xx
\0xx 
```

---

### Post by dcstar on 2009-02-17
> **paskie said:**
> 
.........
I so much hate dpkg for botching up this license stuff and taking 40 minutes of my life now...

Yes, it must be the fault of dpkg that something that the application provider **insists** be acknowledged manually is a pain to be acknowledged in another way completely bypassing the wishes of the commercial provider generously allowing you the free use of their software.

Those dpkg package developers are so deserving of "hate" for making something that actually works as it is supposed to...... not.

---

### Post by markba on 2009-03-04
This is another solution:

```
echo sun-java6-jre shared/accepted-sun-dlj-v1-1 select true | /usr/bin/debconf-set-selections
apt-get install --yes sun-java6-jre
```

Works for me...

Found it here: [http://www.davidpashley.com/blog/debian/java-license](http://www.davidpashley.com/blog/debian/java-license)

---

### Post by cmay on 2009-03-04
thats strange.
when i run this script below there is an message in the terminal that the license is alreay agreed upon and i never have to do anymore than just run the script and wait for it to finish. i do not know why so i ponder about this a bit. 
[PHP]#! /bin/bash
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libavcodec-unstripped-51 libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar xine-ui[/PHP]

---

