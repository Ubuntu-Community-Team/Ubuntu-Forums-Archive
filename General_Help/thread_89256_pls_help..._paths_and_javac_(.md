---
title: "pls help... paths and javac :("
date: 2005-11-12
forum: General Help
---

### Post by trandojedi on 2005-11-12
hi... i want to beble to use javac by just entering:

...@ubuntu:javac

instead of
...@ubuntu:./opt/jdk<version>/bin/javac

how would i go about doing this? i've searched a bit on her and i believe it relates to path (/ect/profile file)... what exactly do i do.. pls be specific cause i didn't understand some of the other post... oh and hehe wtf is like ~/.blahblah mean is it a file or a director i don't get the whole '~' thing...

cheers if someone could help me out with this :)

---

### Post by shandar on 2005-11-12
Not sure about the path-thingy, how did you install the JDK? I used fakeroot and jpkg to convert the bin then installed the .deb that was created. It worked perfectly. Check this link for instructions: [https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca](https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca) but download the JDK instead :)

~ is short for your home directory, /home/<username>/ so ~/blahblah is /home/<username>/blahblah

---

### Post by hunt.topher on 2008-02-19
I've found one solution, maybe not the best, but at least it's a fun approach.

I've found it frustrating that even in Gutsy, I have trouble getting Java set up well initially without some toying around. On my first laptop I played around with packages in Synaptic for a month and finally got javac working without resorting to the terminal. Then I got a NEW laptop and forgot to use dpkg --get-selections to get a list of all the packages I had installed, so on this problem I had to start from scratch... I just found a solution that seems to do the trick.

I have used Synaptic to install the sun-java6 packages: sun-java6-bin, sun-java6-fonts, sun-java6-jdk, sun-java6-jre, sun-java6-plugin, sun-java6-source.
The command 'java' worked fine form terminal, but 'javac' didn't.

**BACKGROUND:** Here's how these commands work as far as I can gather: by default, many or most available terminal commands are placed in the directory /usr/bin. When you run these commands from terminal, the terminal looks for a file of that same name in that folder. Because applications are actually installed in multiple directories, many programs only place in that folder a *link* to the actual program. The problem with javac seems to be that the javac link in /usr/bin points to a nonexistent folder and a nonexistent file, so terminal doesn't detect the javac program as being installed. We'll fix this by replacing the broken link in /usr/bin with a new one that works.

**NOTE:** If you have a different version of Java installed that you want to use, you'll need to change the directory </usr/lib/jvm/java-6-sun/bin/javac> that I use in the instructions below. This is the directory where the javac program is hidden, so naturally if you follow the instructions below and that directory doesn't exist, you'll be no better off than before. Check /var/lib/dpkg/alternatives/javac, if the file exists, for a list of possible paths and test them by entering them into your terminal to see if they run the javac program as you want them to.

**MY FIX:**
Open a Terminal window (Applications -> Accessories -> Terminal) and enter:
> cd /usr/bin
to change to the /usr/bin directory. Then create (aka overwrite) the symbolic link by entering:
> sudo ln -s /usr/lib/jvm/java-6-sun/bin/javac
Now test your new link by trying to use javac as normal!

**NOTE:** Hopefully you aren't still waiting on an answer to this problem since 2005! I'm posting this mainly because it seems like a valid problem to me, I haven't found any better solutions, and this forum came near the top of my Google search results.

---

