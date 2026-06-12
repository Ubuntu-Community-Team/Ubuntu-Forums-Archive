---
title: "Here's a way to make Firefox-3.0 more stable."
date: 2008-07-21
forum: General Help
---

### Post by tagra123 on 2008-07-21
Firefox version 2 is and has been very stable for me -- been using it in Hardy. I wanted version 3 of firefox to behave the same way.

I had used ubuntuzilla and firefox's own update utility to keep things up to date in dapper.

Firefox 2 is installed in /opt/firefox using ubuntuzilla in my hardy install

So upgrading to Ubuntu Hardy 8.04 most things went well but today is the day I finally was able to use firefox 3 without constant crashes. The crashes were more like stalls and when starting from console there were no helpful messages displayed and it locked up in a way that the built in crash reporter never even displayed. 

I tinkered with this a few times but finally decided to not take the advice from others who were still having problems with firefox  and tried something different.

I have ran all day today without one firefox 3 crash and its behaving as good as firefox 2 did.

I didn't tinker with the synaptic installed firefox other than renaming two files. 

Here's what I did to get it to work. And if I still want to use version 2 I can.

Download the latest firefox (right now it is 3.0.1)

[http://www.mozilla.com/en-US/](http://www.mozilla.com/en-US/)

extract it -- you can use nautilus

Mine extracted to ~/Desktop/firefox


Open a terminal

Make a backup of you .mozilla directory (just in case)

```
cp ~/.mozilla ~/_mozillabackup_date -f -r
```


Copy firefox to /opt
```
sudo mkdir /opt/firefox-3.0

sudo cp  ~/Desktop/firefox/* /opt/firefox-3.0 -f -r

```


Try it
```
/opt/firefox-3.0/firefox
```

It worked well but there were no plugins.  This part was tricky at first and I wanted it to be setup in a way that I know exactly where all the plugins are -- (not in /etc/alternatives)


To make easy here is here is my list of plugins.

Notice that the symbolic links are full paths/

To create the symbolic link to the adobe reader the command is

```
sudo ln -s /usr/lib/Adobe/Reader8/Browser/intellinux/nppdf.so /opt/firefox-3.0/plugins/nppdf.so
```

You can repeat for each of the following links.

```
me@mymachine:/opt/firefox-3.0/plugins$ ls -lah
total 32K
drwxr-xr-x  2 root root 4.0K 2008-07-21 15:17 .
drwxr-xr-x 14 root root 4.0K 2008-07-21 14:39 ..
lrwxrwxrwx  1 root root   37 2008-07-21 15:17 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
lrwxrwxrwx  1 root root   64 2008-07-21 15:13 libjavaplugin_oji.so -> /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
-rwxr-xr-x  1 root root  16K 2008-07-21 15:06 libnullplugin.so
lrwxrwxrwx  1 root root   38 2008-07-21 15:04 mozplugger.so -> /usr/lib/mozilla/plugins/mozplugger.so
lrwxrwxrwx  1 root root   46 2008-07-21 15:04 mplayerplug-in-dvx.so -> /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
lrwxrwxrwx  1 root root   47 2008-07-21 15:04 mplayerplug-in-dvx.xpt -> /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
lrwxrwxrwx  1 root root   45 2008-07-21 15:04 mplayerplug-in-qt.so -> /usr/lib/mozilla/plugins/mplayerplug-in-qt.so
lrwxrwxrwx  1 root root   46 2008-07-21 15:04 mplayerplug-in-qt.xpt -> /usr/lib/mozilla/plugins/mplayerplug-in-qt.xpt
lrwxrwxrwx  1 root root   45 2008-07-21 15:04 mplayerplug-in-rm.so -> /usr/lib/mozilla/plugins/mplayerplug-in-rm.so
lrwxrwxrwx  1 root root   46 2008-07-21 15:04 mplayerplug-in-rm.xpt -> /usr/lib/mozilla/plugins/mplayerplug-in-rm.xpt
lrwxrwxrwx  1 root root   42 2008-07-21 15:04 mplayerplug-in.so -> /usr/lib/mozilla/plugins/mplayerplug-in.so
lrwxrwxrwx  1 root root   46 2008-07-21 15:04 mplayerplug-in-wmp.so -> /usr/lib/mozilla/plugins/mplayerplug-in-wmp.so
lrwxrwxrwx  1 root root   47 2008-07-21 15:04 mplayerplug-in-wmp.xpt -> /usr/lib/mozilla/plugins/mplayerplug-in-wmp.xpt
lrwxrwxrwx  1 root root   43 2008-07-21 15:04 mplayerplug-in.xpt -> /usr/lib/mozilla/plugins/mplayerplug-in.xpt
lrwxrwxrwx  1 root root   50 2008-07-21 14:57 nppdf.so -> /usr/lib/Adobe/Reader8/Browser/intellinux/nppdf.so
lrwxrwxrwx  1 root root   36 2008-07-21 15:09 nsdejavu.so -> /usr/lib/mozilla/plugins/nsdejavu.so
lrwxrwxrwx  1 root root   64 2008-07-21 15:13 xulrunner-1.9-javaplugin.so -> /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so

```

Once you have linked to the plugins you want to use then you can get the firefox in /opt to work for your menus and terminal.


cd /usr/bin

Backup originals
```
mv firefox firefox.old
mv firefox-3.0 firefox-3.0.old
```

Create links to the new firefox
```
ln -s /opt/firefox-3.0/firefox /usr/bin/firefox
ln -s /opt/firefox-3.0/firefox /usr/bin/firefox-3.0

```



If you find an easier way please post. 


I still am trying to find out why the synaptic installed version fails to work. I could have use ubuntuzilla to do this but it would have overwritten my firefox 2 install in /opt/firefox.

This worked well for me and hope it helps some others.

---

### Post by aysiu on 2008-07-22
This is my easier way:
[http://www.psychocats.net/ubuntu/firefox#terminal](http://www.psychocats.net/ubuntu/firefox#terminal)

---

### Post by tagra123 on 2008-07-22
Thanks asyiu.

I think there is something conflicting my system generated plugins folder. Not sure what though. I did it this way to see if loading plugins -- one at a time I could find the cause -- nothing made it crash. 

Actually I don't get it because plugins between the system installed version and this version are very similar yet the system installed version is unusable.

Before -- PayPal crashes, Gmail Crashes, NOAA crashes, ebay has problems, and sometimes it would even fail to load the ubuntu start page which I thinnk is really odd. 

Now it all works and seems to be as rock solid as version 2.

LIke I said earlier, now that the mozilla version is working I may compare the folders files and links in the working version to the system installed version and see if I can find out why the system version crashes so much.

Is there a diff for directorys?

---

### Post by nanotube on 2008-07-22
> **tagra123 said:**
> 

I still am trying to find out why the synaptic installed version fails to work. I could have use ubuntuzilla to do this but it would have overwritten my firefox 2 install in /opt/firefox.

This worked well for me and hope it helps some others.

well, all of that ubuntuzilla basically does for you automatically.
so if you wanted to keep your ubuntuzilla firefox2 in /opt/firefox, all you had to do is ```
mv /opt/firefox /opt/firefox2
```

and then use ubuntuzilla to install ff3 to /opt/firefox. then you'd have ff2 in /opt/firefox2, and ff3 in /opt/firefox

alternatively... you could have left ff2 where it is, and used ubuntuzilla with the "-r targetdir" option:
```
ubuntuzilla.py -a install -p firefox -r /opt/firefox3
```

that would stick ff3 into /opt/firefox3/firefox/, leaving your old ff2 in /opt/firefox untouched.

just some tips for the future. :)

---

### Post by geezerone on 2008-07-22
The latest release of firefox (3.0.1) is available for download on linux as well as the other two OSes. When will this update appear in the repositories?

---

### Post by tagra123 on 2008-07-22
> **nanotube said:**
> well, all of that ubuntuzilla basically does for you automatically.
so if you wanted to keep your ubuntuzilla firefox2 in /opt/firefox, all you had to do is ```
mv /opt/firefox /opt/firefox2
```

and then use ubuntuzilla to install ff3 to /opt/firefox. then you'd have ff2 in /opt/firefox2, and ff3 in /opt/firefox

alternatively... you could have left ff2 where it is, and used ubuntuzilla with the "-r targetdir" option:
```
ubuntuzilla.py -a install -p firefox -r /opt/firefox3
```

that would stick ff3 into /opt/firefox3/firefox/, leaving your old ff2 in /opt/firefox untouched.

just some tips for the future. :)


I was aware of this  and had already tried firefox 3 using zilla.  It didn't work right either. When installed with ubuntuzilla I believe it uses the default plugins that the synaptic version was using because the crashing continued.  I wanted a clean install with no plugins and no extensions. 

I did it this way so #1 I could easily revert to firefox2 if it wasnt working and #2 I could easily add a plugin at a time to see what caused the crash. The funny thing is it didn't crash at all with the plugins using the manually installed version.  It's still working perfectly.

 I've looked at the plugins directory in /etc/alternatives /usr/lib/mozilla and /usr/lib/firefox.  The only difference I see is the symbolic links. The links in the /usr/lib/firefox/plugins are not full path links they are relative and the links in /opt/firefox-3.0/plugins are absolute (full path links). I dont believe that this could be the source of the problem and I'll keep looking but it's nice to be able to use firefox 3 finally.

I like scripts as much as the next guy/gal, but in this case I wanted a little control over what was being placed in the plugins directory and this worked well.

Thanks for the comment though.

Actually I had copied the /opt/firefox to /opt/firefox.bak to backup version 2 before installing using ubuntuzilla -- when firefox 3 still crashed when installed from zilla I deleted /opt/firefox and renamed /opt/firefox.bak to /opt/firefox.

---

### Post by mc4man on 2008-07-23
> The latest release of firefox (3.0.1) is available for download on linux as well as the other two OSes. When will this update appear in the repositories? it's available in the hardy-proposed repo

---

### Post by geezerone on 2008-07-23
Thanks. Wondered where it was. The jump from FF2 -> FF3 was quicker without the proposed repo.

---

