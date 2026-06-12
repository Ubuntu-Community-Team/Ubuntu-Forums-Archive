---
title: "install java and flash on firefox 3.5 (non repo ver)"
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by v1nsai on 2009-08-06
I downloaded the new firefox binary from firefox.com and switched the symlinks around in /usr/bin to point to 3.5.

That went fine, however I'm having trouble installing java and flash plugins now.  The .mozilla folder used to have all the plugins installed and I would have been able to just transfer them to the plugins folder used by 3.5, but it seems to have changed since the last time I used it and I can't find the plugins folder in .mozilla.

Can someone tell me where the plugins are stored for the repo version of firefox or tell me how to install java and/or flash on 3.5?  I've tried googling around but all I've found are guides for installing the java runtime in linux.  I most definitely have the jre installed already (and jdk actually) so I just need the plugin and I can't find it by itself.

---

### Post by running_rabbit07 on 2009-08-06
> **v1nsai said:**
> I downloaded the new firefox binary from firefox.com and switched the symlinks around in /usr/bin to point to 3.5.

That went fine, however I'm having trouble installing java and flash plugins now.  The .mozilla folder used to have all the plugins installed and I would have been able to just transfer them to the plugins folder used by 3.5, but it seems to have changed since the last time I used it and I can't find the plugins folder in .mozilla.

Can someone tell me where the plugins are stored for the repo version of firefox or tell me how to install java and/or flash on 3.5?  I've tried googling around but all I've found are guides for installing the java runtime in linux.  I most definitely have the jre installed already (and jdk actually) so I just need the plugin and I can't find it by itself.

An easy way to get the flash plugin is to go to myspace.com and you will be offered Adobe and 2 others to choose from.

---

### Post by v1nsai on 2009-08-06
I don't know why that worked, but it did *backs away slowly*

Thanks for that, that's one down.  Any idea where plugins are stored?  I'm pretty sure they're not in .mozilla anymore

---

### Post by threedogsandababy on 2009-08-06
You have an option or two here. firefox-3.5 is indeed in the repos now if you're using Jaunty. When you run it, it will say Shiretoko, but it is indeed a full version of 3.5. If you use this method, your plugins will be detected. They're in /usr/lib/mozilla/plugins/. 

Now, if you're determined to use the downloaded binary from Mozilla, you'll need to: sudo cp /usr/lib/mozilla/plugins/* ~/locationoffirefoxfolder/firefox/plugins/

If you have flash installed, it should just work. If not: sudo apt-get install flashplugin-nonfree (do this before copying your plugins over)

I also like to use gecko-mediaplayer for watching movies in Firefox, also. Works much better than any other plugin. It's becoming the defacto replacement for the mplayer plugin (it uses a frontend to mplayer I believe, so mplayer, gnome-mplayer and dependencies will be installed). 

Now, I use the sun-java6-plugin for java, it's the ONLY one apart from sun-java5 that works without incident with Pogo games. I play chess daily, so I need the plugin. To get it: sudo apt-get install sun-java6-plugin

So to recap. If not done already...

sudo apt-get remove totem-mozilla && sudo apt-get install flashpluing-nonfree sun-java6-plugin gecko-mediaplayer

sudo cp /usr/lib/mozilla/plugins/* ~/locationoffirefoxfolder/firefox/plugins

*** in Firefox 3.5, I need to remove the default java plugin, which you can then do in your Firefox plugins folder in your /home installation of Firefox, or in /usr/mozilla/plugins/ if you go the Shiretoko route. Then do this: sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.14/jre/plugin/i386/ns7/libjavaplugin_oji.so ~/locationoffirefoxfolder/firefox/plugins/  or sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.14/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla/plugins/ depending on how you install FF 3.5.

That's it. It's a pain, but it works.

---

### Post by v1nsai on 2009-08-06
Thanks 3dogs, I picked up shiretoku a little while ago and forgot that I was using it when I thought that flash had suddenly started working.  Shiretoku still hadn't picked up the java plugin for some reason, but running sudo apt-get install sun-java6-plugin worked for me.  I never thought to try that since I had already installed that package.  Thanks a bunch though.

One more question though, where are the plugins for shiretoku saved at?  I'd just like to know so I can manually install something if I run into trouble.

---

### Post by running_rabbit07 on 2009-08-06
> **v1nsai said:**
> I don't know why that worked, but it did *backs away slowly*

Thanks for that, that's one down.  Any idea where plugins are stored?  I'm pretty sure they're not in .mozilla anymore

That was just one of the first sites I went to when I installed Ubuntu the first time and made note of the plug-in options.

---

