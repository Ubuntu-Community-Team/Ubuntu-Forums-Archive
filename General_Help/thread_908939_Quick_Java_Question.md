---
title: "Quick Java Question"
date: 2008-09-03
forum: General Help
---

### Post by Nate9009 on 2008-09-03
To make a long story short, I'm posting on behalf of my brother who happens to be a avid player of a online java-based MMORPG called Runscape.

He told my my computer (the only one working in the house) can't play the game without crashing after a few minutes. The game crashes whenever he visits certain map areas.

If you are running a PC with 1GB+ of RAM, a memory conflict can occur. This problem is caused by Java not giving RuneScape enough memory to work with and can be solved using the following steps.

Note: Please only perform these steps if you are technically competent or a responsible adult. Jagex takes no responsibility for any data lost as a consequence of using this fix.

   ```
. Open your Windows Control Panel

   2. Open the Java Control Panel

   3. Select the Java tab (highlighted at the top of the image to the right)

   4. In the "Java applet runtime settings" section choose "View..." (highlighted in the image to the right)

   5. Your JRE version should be listed there. In the box marked run-time parameters, you can add something like:

      -Xmx256M

      Include the minus sign before it. This should increase the maximum available memory to Java to 256MB. Do not set this number to anything more than half of your maximum RAM otherwise Windows could have problems running.

      The image below highlights the box (or boxes) you will need to adjust. 



As Runescape is designed to be run on Windows using the Internet Explorer browser software, we can only offer support relating to those products. If you are using a different operating system or browser then you will have to consult the manual for that software to find the equivalent procedures. 

I figured it was a problem with the game not my computer, as I have never had a java-related problem before.

After checking it out a bit I found a section under the technical help section of the site that has a solution for Windows to fix the problem he was having.

```

Java Version : java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)

I tried completely reinstalling Java as well as deleting the cache.  Neither have worked.

Any ideas on what I should do?

---

### Post by tuxxy on 2008-09-03
What java version are you using

---

### Post by Nate9009 on 2008-09-03
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)

:guitar:

---

### Post by Oldsoldier2003 on 2008-09-03
Please dont add irrelevant tags to threads, it hinders effective tag searching and dilutes the usefulness of the feature.

---

### Post by jamesstansell on 2008-09-03
> **Nate9009 said:**
> java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)

:guitar:

That's version 6u3, which is fairly old; the current version is 6u7.

What version of ubuntu?  What browser, and version?

Honestly, I've never experienced runescape crashing, although I have neither played it frequently nor recently.

Before Ubuntu 8.04 the flash plugin would frequently crash firefox, but I assume that it's not related to this issue.

---

### Post by Denestria on 2008-09-04
I play Runescape with java version 1.6.0_07 and it runs fine.  The only problem I have is when exiting the game Firefox crashes, but at that point it doesn't matter and has no effect on the game.

---

