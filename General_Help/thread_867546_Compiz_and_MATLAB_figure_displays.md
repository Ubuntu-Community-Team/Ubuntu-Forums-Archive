---
title: "Compiz and MATLAB figure displays"
date: 2008-07-23
forum: General Help
---

### Post by EVA01 on 2008-07-23
Hello everyone. I'm new to this forum, as well as fairly new to Ubuntu (8.04). I'm a recent convert from Windows, and I've been using Linux for research applications. I've also had to rely quite a bit on threads on this forum to get by. :)
Anyways, I've been running Compiz so I can get those cool desktop effects and also the Avant Window Manager. However, it has been interfering with my work using MATLAB: every once in a while, I'll try to plot a figure, and the figure will not show up or it will maximize across the entire screen and not show any actual figure. I'm guessing there's some kind of compatibility issue between Java and Compiz? Some Java programs with GUIs I've tried to run have a similar issue, where the contents of a frame won't show up or something.
Unlike a lot of what I've already seen on the forums, my MATLAB will start and run pretty smoothly - it's just the figures.

Thanks! If any other details are required, let me know.

---

### Post by h3nk on 2008-07-24
[http://ubuntuforums.org/showthread.php?t=812791](http://ubuntuforums.org/showthread.php?t=812791)

i had problems with maple and compiz and it solved my problems. so if matlab is java-based this might also help you

---

### Post by fsr_elite on 2008-11-23
This won't help, but maybe it will bump the thread, or someone will point us to a solution. I am having the same trouble, and it is driving me crazy. (It will work if I turn off Compiz, but I don't like doing that -- "Scale" is too useful).

---

### Post by Rasheeke on 2008-12-02
I'm having the same problem where I'm trying to open 2 figures, the first one shows up fine while the second one is maximized with the window itself straddling two workspaces and part of the figure shows on the top left and I can interact with it, fully maximizing onto the current workspaces and I see that one part of the figure adjust to the maximizing but the rest of the figure stays gray or has many horizontal lines while the top left of the figure is as it should be.

Closing the figure and re opening over and over and eventually the 2nd figure would open normally as the 1st but it's pretty hit or miss. 

Don't really know the much about my computer since it's a work computer, not to sure what kind of graphics card I have nor do I know how to find out so finding new drivers is difficult.

---

### Post by nmaster on 2009-06-17
I've been having the same problems, but only with plots played in series to make a movie.  I'm not sure why.  It used to work, but then I installed Mac4Lin.  I'll just try removing all the compiz stuff.  Hopefully that'll work.

---

### Post by opto09 on 2009-06-30
Hi just wondering if anybody has managed to find a workaround for this. I'm having the same problem running Matlab 2008a in Jaunty.

---

### Post by nmaster on 2009-07-02
bump

---

### Post by XCan on 2009-07-02
What JRE are you using? I know if you use openJDK then all kind of weird stuff will happen.

---

### Post by opto09 on 2009-07-13
I'm not 100% sure... how do you tell?

If I use java- -version I get,

```
$java -version
java version "1.6.0_13"
Java(TM) SE Runtime Environment (build 1.6.0_13-b03)
Java HotSpot(TM) 64-Bit Server VM (build 11.3-b02, mixed mode)
```

---

### Post by XCan on 2009-07-13
That seems right. It's the same JRE as I am using (Sun's).

---

### Post by Xyro on 2009-08-12
This seems to have solved my problems (same as OP):

[http://ubuntuforums.org/showthread.php?t=635142](http://ubuntuforums.org/showthread.php?t=635142)

The "new solution" is the one that did it for me (only one I tried).

Summary:

Add the line

```
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre/
```
... to the run script for Matlab (wherever you told it to put the symbolic links during install, and likely the script you call to run Matlab). Mine happens to be located at:

```
/usr/local/bin/matlab
```
Your script should look something like this (courtesy of Breathe in above link):

```

#!/bin/sh

export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre/

#
# Name:
# matlab script file for invoking MATLAB
#

bla bla bla

```
Obviously, you should also have the latest Sun Java installed. Hope this helps.


~Xyro


[SIZE="1"]Matlab figure Java Compiz[/SIZE]

---

### Post by MRIDENTI on 2009-08-13
I've found a workaround to the Matlab figure bug when running in Jaunty. 

I launched the "Appearance Preferences" window and I selected "None" in the "Visual Effects" tab. Since then, I haven't observed that bug in Matlab. 

I think it will be useful for those who do not use visual effects.

---

### Post by opto09 on 2009-08-19
Thanks Xyro. Will have a try of it once I get into work.:)

---

