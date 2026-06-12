---
title: "KDE 3.5 RC1 &amp; arts still crashing"
date: 2005-11-16
forum: General Help
---

### Post by patsissons on 2005-11-16
I just recently upgraded to the 3.5 RC1 for breezy.  I was a little disapointed to find that arts still isn't working properly.  I did some research and some said that disabling the realtime priority fixed the crashing.  Oddly enough, it was not the realtime priority but rather the full duplex mode that was causing that infinite crash loop.  This is kind of odd, since I am using a SB Live 5.1 card.

Just wondering if anyone is experiencing this issue.  I haven't been able to test whether or not the full duplex is really affected since i don't have any apps that currently need full duplex.  Maybe i'll install some sort of VOIP style app sooner or later and test it out.

---

### Post by Wizzard on 2005-11-17
Are you sure you fully upgraded your KDE? Are not there any broken packages or dependencies? I do not have a single problem with KDE RC1 already.

---

### Post by Shanachie on 2005-11-18
Hello,
I had the same problem and fixed it by installing akode, apparently it was not installed. I noticed the missing dependency by running artsd in a terminal after it crashed once again.

Hope this helps some people.

---

### Post by ace2005 on 2005-11-18
I had a very similar problem, KDE 3.5 RC1 installed fine and there were no broken packages, i did it through synaptic in the failsafe terminal so it would have told me.

All the latest packages were installed at the time.

Everything seemed to work perfectly, the sound server didn't crash and kde looked very nice.

However Juk crashed on startup, it was the latest version of juk too. So i added the repositories from Beta 1 and then used synaptic to force version, it got rid of some KDE too but now everything works fine,

One of the dev packages for kde, i can't remember which one has a dependency on arts-dev, the version from KDE 3.5 RC1 which has a dependency on arts from KDE RC1, which if installed will screw up Juk again so i got the kde dev package from the repo myself and installed it using --force-depends. I needed it to install themes and window borders, whats the point of getting KDE 3.5 RC1 if i can't make it look good?

KDE 3.5 is working very well, the transparency works well too but sometimes it freezes up totally and xorg becomes a resource hog but i think this is because its new, can't wait for KDE 4

---

### Post by wrtrdood on 2005-11-18
I ran through this too.  I tried several approaches that never seemed to work.  There were some dependencies that just did not seem to get picked up so I used aptitude instead and it managed to install/upgrade a bunch of libs that got missed.  After using aptitude, everything is working great.  You might want to give it a try.

---

### Post by patsissons on 2005-11-19
[QUOTE=Shanachie]Hello,
I had the same problem and fixed it by installing akode, apparently it was not installed. I noticed the missing dependency by running artsd in a terminal after it crashed once again.

Hope this helps some people.[/QUOTE]

It did help, thank you very much, arts appears to be working almost as it should.  I still have the full duplex issue.  I know the card can handle full duplex because it used to when i had kde 3.4 installed.  Could this possibly be an issue with one of the configuration files for the soundcard itself?

---

