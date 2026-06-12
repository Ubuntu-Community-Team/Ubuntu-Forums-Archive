---
title: "Firefox 1.5 problems."
date: 2005-11-30
forum: General Help
---

### Post by Bandit on 2005-11-30
Hey All,
Firfox 1.5 is out. But for some strange reason I cant get it to work and it look like its on Mozilla's end..
It complains when you go to run the binary that libstdc++.so.5 cant be found..
Error missing shared library..
Shouldnt this be in the same folder as firefox?
Going by mozilla's instructions you can run it directly from the folder.. supposedly that is...
Anyone having these issue's as well?
Cheers,
Joey

---

### Post by Curlydave on 2005-11-30
After unpacking it, just run the script with the name "firefox".

Try this:

Unpack it in your main / directory. It should create a folder called "firefox". Create a launcher on the desktop, and enter the following command in it: "/firefox/firefox". Run the launcher. Let me know if that works. 

I don't know if it's because of 1.5 or because I'm running it from teh directory instaed of the one embedded in the filesystem, but now FF is MUCH faster, up to the speed it is in Windows. Can anyone confirm if this is caused by 1.5 or by running it from a directory?

---

### Post by mustang on 2005-11-30
That's weird. I never encountered that problem. Did you try

sudo apt-get install libstdc++5

?

---

### Post by Chippendale on 2005-11-30
all i did for the libstdc++ dependecy is check in Synaptic Package Manager if i had it installed. I did so i continued with the installation 


heres the wiki HOWTO in case you've missed it

[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

---

### Post by endersshadow on 2005-11-30
Anybody know if it'll be going into main soon?

---

### Post by ad noiseam on 2005-11-30
[QUOTE=endersshadow]Anybody know if it'll be going into main soon?[/QUOTE]

Read [this thread](http://www.ubuntuforums.org/showthread.php?t=96595). It will probably not be available for a while, as it is a big change that needs to be worked on carefully.

---

### Post by RAOF on 2005-11-30
I don't think it'll be going into main.  It's a big change from firefox 1.0.7, and pretty much only bugfixes and security fixes get added to the (main) Breezy repos from now on.

On the other hand, you can expect it in the (semi-supported) dapper backports repo pretty soon, I'd imagine :)

Edit: Or, looking at the thread above, sometime in the future.  That's a **lot** of work!

---

### Post by Bandit on 2005-11-30
I have libstdc++6, if I go to libstdc++5 I have to downgrade to gcc3.4. I have gcc4 installed and would much rather stay with that.
So I guess I am SOL.
Cheers,
Joey

---

### Post by endersshadow on 2005-11-30
[QUOTE=ad noiseam]Read [this thread](http://www.ubuntuforums.org/showthread.php?t=96595). It will probably not be available for a while, as it is a big change that needs to be worked on carefully.[/QUOTE]

Bummer.  Guess I'm gonna have to stop being lazy and compile from source.

Thanks for the info!!

---

### Post by RAOF on 2005-11-30
[QUOTE=Bandit]I have libstdc++6, if I go to libstdc++5 I have to downgrade to gcc3.4. I have gcc4 installed and would much rather stay with that.
So I guess I am SOL.
Cheers,
Joey[/QUOTE]
You shouldn't have to downgrade anything.  libstdc++6 & libstdc++5 are parallel installable.  I, myself, have both installed (and gcc-3.4 & gcc-4 & ...)

You shouldn't need to compile from source, either.  I downloaded the one of the binary RCs and that ran fine (except for [a certain amount of fiddling to get the 32bit binary working on an amd64 system]("http://www.ubuntuforums.org/showthread.php?t=90106").  On an x86 system it should work fine with no fiddling :))

---

### Post by Bandit on 2005-11-30
[QUOTE=RAOF]You shouldn't have to downgrade anything.  libstdc++6 & libstdc++5 are parallel installable.  I, myself, have both installed (and gcc-3.4 & gcc-4 & ...)

You shouldn't need to compile from source, either.  I downloaded the one of the binary RCs and that ran fine (except for [a certain amount of fiddling to get the 32bit binary working on an amd64 system]("http://www.ubuntuforums.org/showthread.php?t=90106").  On an x86 system it should work fine with no fiddling :))[/QUOTE]
I do lots of compiling. Matter of fact I just compiled Gstreamer 0.9.6 and Rhythmbox 0.9.2. But if they will work parrell with each other I will try again :D
Thanks,
Joey


!!!UPDATE!!!
It runs... It also blows using dark themes.....
Not realy sure I like this new FF, but I will try it out for a while...
Think they have a few bugs that need attention. I will let them know..
Cheers,
Joey

---

