---
title: "Firefox 3 Java Web plugin"
date: 2008-07-28
forum: General Help
---

### Post by kai_tea on 2008-07-28
Hi, I've been looking around on this forum and the internet A LOT on how to get the Java web plugin working. I have java 6 installed, it's just the fx plugin that I can't get up and running. I tried inputting a number of things into the terminal that I found online. None of which worked for me. I tried the gcj plugin found in the synaptic package manager. That made things worse (I was using Yahoo! Games (Yahoo! Pool to be precise) as a test to see if it would work and it kept telling me that java wasn't there/wasn't working and when i enabled gcj i couldn't even load the page and then firefox would crash/close itself when i tried to load the Yahoo! Pool page).

So I was wondering if anyone could give me any suggestions. Any help would be much appreciated. Please note though, that I've only logged about 5 days of time actually using Ubuntu so this is all very very very new to me. Please be as detailed as possible. Thanks.

---

### Post by Lakjin on 2008-07-28
I dont understand why you are having a problem. I have Java 6 installed and everything is working fine. I just tested Yahoo Pool also.

---

### Post by kai_tea on 2008-07-28
weird.. you think i have some other stuff installed that might be interfering?

---

### Post by kai_tea on 2008-07-29
> **Lakjin said:**
> I dont understand why you are having a problem. I have Java 6 installed and everything is working fine. I just tested Yahoo Pool also.

wait a sec, are you using 32-bit? i'm running 64-bit amd processor and that's why i can't install the fx plugin that comes with it. the plugin says it is not compatible with amd64... maybe i should wait until a fix is released? but would that come netime soon?

can anyone offer insight/suggestions or does anyone have a firefox java plugin working on a amd64 machine?

---

### Post by kai_tea on 2008-08-01
so no one knows a fix?

---

### Post by mcgarry83 on 2008-08-09
Im having the same problem, I wanted to play a Yahoo game and the page comes up that says something like "please check to see if you have Java installed". I also have ver6 installed with the firefox plug-in. Not sure what to do.

---

### Post by shawncorn on 2008-08-10
I just got mine working.

I went into Synaptic, searched for "jre".

I removed all the "icedtea" packages that came up:
openjdk-6-jre
openjdk-6-jre-headless
openjdk-6-jre-lib
icedtea-java7-jre

I removed the java5 packages:
sun-java5-bin
sun-java5-fonts
sun-java5-jre
sun-java5-plugin

I checked to reinstall sun-java6-plugin.

After applying it and restarting firefox, I went into the Tools->Add-ons->Plugins section and made sure Sun Java plugin was enabled (it had said iced tea before this).  Then yahoo worked fine again.

I don't care to research this further, but if I had to take a guess, I'd say that ubuntu is shipping with some free java alternative which yahoo doesn't play with nicely.  The solution is to use Sun's implementation.

---

### Post by meitetsuman on 2008-08-12
I got java working by clicking on the "Applications" tab.  Then I clicked on "Add/Remove".  Then I chose "all Open Source applications" and in the search box I put "java".  Then click the box by "Icedtea Java plugin" and click "apply changes".  Worked for me (at least I think that's what did it).

---

