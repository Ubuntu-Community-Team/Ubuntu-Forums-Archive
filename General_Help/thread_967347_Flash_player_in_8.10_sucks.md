---
title: "Flash player in 8.10 sucks"
date: 2008-11-01
forum: General Help
---

### Post by Samueltehg33k on 2008-11-01
yeah so youtube videos in 8.10 freeze every couple of seconds in epiphany and firefox this only is an issue in 8.10 and many of my friends are having the same issue

---

### Post by LaRoza on 2008-11-01
> **Samueltehg33k said:**
> yeah so youtube videos in 8.10 freeze every couple of seconds in epiphany and firefox this only is an issue in 8.10 and many of my friends are having the same issue

It is Flash 10. I use it with no problem on 64 bit Ubuntu with Opera.

---

### Post by K.Mandla on 2008-11-02
Moved to General Help.

---

### Post by Irishpolyglot on 2008-11-02
Also having the same issue since updating Ubuntu. Embedded Youtube videos play perfectly for about 10 seconds and then just stop and white-out.
I'm in 8.10 and according to about: plugins I'm using Flash 10.

---

### Post by Interpreter on 2008-11-02
Yupp FLASH 10 worked fine under HH and now crashes way too often to be ignored.

---

### Post by Sef on 2008-11-02
1) How did you upgrade to Ibex?

2) Are you all using 32-bit?

3) How did you install flash?

---

### Post by Irishpolyglot on 2008-11-02
Sef,
1) I set "Normal releases" in Software Sources-> Updates and 8.10 was installed automatically.
2) Yes
3) I didn't update flash. I was using the old version before upgrading and it seems to have updated itself to flash 10. I'd rather find a solution in v.10 than downgrade because I had some instability before too (but nothing as bad as right now)

Just in case it's related, note that I am forced to [login through Failsafe Gnome]("http://ubuntuforums.org/showthread.php?t=966781") at the moment. (Help on that other thread appreciated!!) But I doubt hardware/video issues are involved because the video plays nice and crisply for 10 seconds before it crashes.

Not just Youtube, but other site's embedded videos do the same. Thanks for suggestions!

---

### Post by steveneddy on 2008-11-02
Does Flash 10 work correctly in FF3 in Intrepid?

Or do the drop down menus drop under the main Flash video on a web page?

My thread regarding this issue.

[http://ubuntuforums.org/showthread.php?t=967764](http://ubuntuforums.org/showthread.php?t=967764)

---

### Post by Irishpolyglot on 2008-11-02
Your thread refers to mixing flash installations, do you think that's related? I never uninstalled flash 9.

To answer your question, we are all in Intrepid. I didn't realize it before, but yes - accessing the menu is limited and immediately crashes the video (not accessing it still lets the video play for a few seconds). Also I notice that the video part has dotted selected lines around the box. That never happened before. The video continues playing sometimes with sound clearly audible even though the video itself has vanished.

---

### Post by Interpreter on 2008-11-03
I for one am crashing with Opera ;)

---

### Post by causeitsme on 2008-11-03
Epiphany and Firefox crashing on pages with embedded Flash.

 2.6.27-7-generic #1 SMP Thu Oct 30 04:12:22 UTC 2008 x86_64 GNU/Linux

---

### Post by tuxxy on 2008-11-03
Flash 10 in Intrepid is excellent for me, not a single npviewer or browser crash in either FF3 or Opera 9.62  since the beta release! ;)

---

### Post by BetterSense on 2008-11-03
This is making Firefox unusable for me, I think. Opening web pages with embedded videos makes firefox crawl and sometimes just freeze outright. It's to the point I can't surf the web with my computer. I upgraded using the update manager from Hardy Heron. Is there anyway I can roll back to flashplugin 9?

---

### Post by causeitsme on 2008-11-03
Ok, just got mine fixed.

*_Note: I'm running 64 bit so if you are on 32 bit this isn't for you._*

It had crashed so I went to Synaptic and installed flashplugin-nonfree. That didn't help anything so I went back to Synaptic and completely removed flashplugin-nonfree. I then googled and found this link: [http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/]("http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/") 

Completely fixed mine.

*Edit: I guess I should've said this before but I copied the code on the page I linked to. Not the Intrepid page.* 

In other words, I put in terminal --> ```
wget http://queleimporta.com/downloads/flash10_en.sh && sudo chmod +x flash10_en.sh && sudo sh ./flash10_en.sh
```

---

### Post by occams_beard on 2008-11-03
Just to add my $0.02, I am also noticing problems with flash 10.  Videos don't freeze up for me, but if a page has any embedded flash, Firefox gets all sluggish. 

For example, I'll be scrolling through a long page, and when I scroll past any flash content, scrolling starts to lag really bad. Very annoying.

---

### Post by Irishpolyglot on 2008-11-04
Weird. I posted above that it was crashing after a few seconds, but now for some reason it's working better and I can watch whole videos. I didn't update anything related to flash etc. But the video still lags and pauses occasionally while the audio continues.

---

### Post by Irishpolyglot on 2008-11-07
Bah! Now it's back to crashing after a few seconds again today and yesterday. I don't think the issue is flash itself since I have the same flash installed for Epiphany and that's working perfectly for all videos. All week I've been copying and pasting urls to Epiphany whenever there's a video in it, hasn't anyone got any suggestions for actually solving the problem??
A 32-bit solution appreciated!! :)

---

### Post by Irishpolyglot on 2008-11-08
OK, it's solved for me!
I didn't apply the code given above because it wasn't pertinent to 32 bit. I went into Synaptic and set it to reinstall flash and all dependencies. Now all embedded videos etc. work as normal :)

---

### Post by barsofham on 2008-11-10
How did you get synaptic to reinstall all the dependencies? Is that an option or do I just need to go through each of them and manually reinstall them?

---

### Post by Irishpolyglot on 2008-11-10
I uninstalled everything related to flash and then installed adobe-flashplugin and any similar names with flash that looked useful in different combinations until it worked. Try a combination of adobe-flashplugin and flashplugin-nonfree and flash-plugin with just one or several at once for example and one of the combinations may work for you if you had the same problem I was having. Now it's working absolutely perfectly with no crashes ever (a huge improvement over how it was before upgrading). Hope that helps! :)

---

### Post by Kilz on 2008-11-11
> **causeitsme said:**
> Ok, just got mine fixed.

*_Note: I'm running 64 bit so if you are on 32 bit this isn't for you._*

It had crashed so I went to Synaptic and installed flashplugin-nonfree. That didn't help anything so I went back to Synaptic and completely removed flashplugin-nonfree. I then googled and found this link: [http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/]("http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/") 

Completely fixed mine.

*Edit: I guess I should've said this before but I copied the code on the page I linked to. Not the Intrepid page.* 

In other words, I put in terminal --> ```
wget http://queleimporta.com/downloads/flash10_en.sh && sudo chmod +x flash10_en.sh && sudo sh ./flash10_en.sh
```

The command downloads a script and automatically installs it without giving the person installing it a chance to look at the script. This is as unsafe a practice as cant be done as the script can be changed at any time. Im not saying this script has been. But it is unsafe and should not be trusted. Users should read and understand all scripts they install, especially from 3rd party sites. This is impossible to do if it downloads and automatically installs.

---

