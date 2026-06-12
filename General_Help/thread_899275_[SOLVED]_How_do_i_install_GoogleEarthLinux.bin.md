---
title: "[SOLVED] How do i install GoogleEarthLinux.bin  ??"
date: 2008-08-24
forum: General Help
---

### Post by Thyssenkrupp on 2008-08-24
Yeh,

I dont know how to install a binary.

how do i do it?

---

### Post by bthoward on 2008-08-24
Honestly your best bet is probably to install via the repositories instead.

Google earth is in the Medibuntu repositories.  You can read about them at [http://www.medibuntu.org/]("http://www.medibuntu.org/").

Anyway while there you'll learn how to add the repositories and what they allow you to install.  Long story short follow the bouncing ball below (these instructions are assuming you're running Ubuntu 8.04 (Hardy Heron):

```

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

Once you have completed those two console command strings you will have added the medibuntu repositories and updated your packages lists. 

You can now install google earth by using synaptic or you can run:
```

sudo apt-get install googleearth

```

Or even easier you can click this: [apt://googleearth]("apt://googleearth")

---

### Post by Elfy on 2008-08-24
Indeed that is the easiest way, but to answer the question so that you know how to do so, if the file is on the desktop

```
cd Desktop
sudo chmod a+x *nameoffile*.bin
./*nameoffile*.bin
```

If it's not on desktop - navigate to right folder, you can use tab to autocomplete - eg type G then tab to fill in name, it might take a few goes if you had  more than one file with G

---

### Post by bthoward on 2008-08-24
You can also right click the file and select properties.  Then go to the permissions tab and check allow executing file as a program.  Then click close.  You can now simply double click the file.

---

### Post by Thyssenkrupp on 2008-08-24
Ahh i figured out an easier way of doing it:

Download GoogleEarthLinux.bin

in terminal do:

sh /directorygoogleearthisin/googleearthlinux.bin

and voila, sorted!

---

### Post by K7AAY on 2009-11-02
> **bthoward said:**
> Honestly your best bet is probably to install via the repositories instead.

Google earth is in the Medibuntu repositories.  You can read about them at [http://www.medibuntu.org/]("http://www.medibuntu.org/").

Anyway while there you'll learn how to add the repositories and what they allow you to install.  Long story short follow the bouncing ball below (these instructions are assuming you're running Ubuntu 8.04 (Hardy Heron):

```

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

<snip>

Fails after the first apt-get line with
E: Type '<html>' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list

---

### Post by Dave&quot;B&quot; on 2010-10-14
> **forestpiskie said:**
> Indeed that is the easiest way, but to answer the question so that you know how to do so, if the file is on the desktop

```
cd Desktop
sudo chmod a+x *nameoffile*.bin
./*nameoffile*.bin
```If it's not on desktop - navigate to right folder, you can use tab to autocomplete - eg type G then tab to fill in name, it might take a few goes if you had  more than one file with G


Tried this but still get the following:

[I][B]david@david-Latitude-D620:~$ cd Downloads
david@david-Latitude-D620:~/Downloads$ sudo chmod a+x GoogleEarthLinux.bin
david@david-Latitude-D620:~/Downloads$ ./GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 5.2.1.1588..............................................................
setup.data/setup.xml:1: parser error : Document is empty

^
setup.data/setup.xml:1: parser error : Start tag expected, '<' not found

^
Couldn't load 'setup.data/setup.xml'
[/B][/I]
Something seems amis with setup.xml

---

### Post by oldos2er on 2010-10-14
[http://ca.ubuntuforums.org/showthread.php?p=9923137](http://ca.ubuntuforums.org/showthread.php?p=9923137)

---

### Post by Dave&quot;B&quot; on 2010-10-14
> **oldos2er said:**
> [http://ca.ubuntuforums.org/showthread.php?p=9923137](http://ca.ubuntuforums.org/showthread.php?p=9923137)


Thank you Ann,
Now I will NEVER need Microsoft again ..............

"In life you cannot press the backspace button....................."
Dave"B"

---

