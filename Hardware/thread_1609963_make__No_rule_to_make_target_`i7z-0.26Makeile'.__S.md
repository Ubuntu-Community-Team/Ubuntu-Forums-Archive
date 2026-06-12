---
title: "make: *** No rule to make target `/i7z-0.26/Makeile'.  Stop."
date: 2010-10-31
forum: Hardware
---

### Post by sclagler on 2010-10-31
greetings!

When running make on /i7z-0.26/Makefile I get the following error even when using the -r and-R options.  "make: *** No rule to make target `/i7z-0.26/Makeile'.  Stop."

I don't know if this is the right forum for this and I don't want to clutter it up with debugging logs unless necessary.

I am using ubuntu 10.10 and thought the turboboost display should already be displayed by the "CPU Frequency Scaling Monitor" applet.

I would also like a cpu temperature monitor.  I get a no thermal monitor support when trying to load the "Computer Temperature Monitor" applet.

I am using the following hardware:
           Gigabyte GA-P55-UD6 motherboard
           intel i7 860 "lynnfield processor"
           8GB corsair dominator xmp ddr3 ram

thanks,
 - sheldon

---

### Post by IcarusR on 2010-10-31
Quote from 

[http://www.gnu.org/software/automake/manual/make/Error-Messages.html]("http://www.gnu.org/software/automake/manual/make/Error-Messages.html")

> &#8216;No rule to make target `xxx'.&#8217;
&#8216;No rule to make target `xxx', needed by `yyy'.&#8217;
    This means that make decided it needed to build a target, but then couldn't find any instructions in the makefile on how to do that, either explicit or implicit (including in the default rules database).

    If you want that file to be built, you will need to add a rule to your makefile describing how that target can be built. Other possible sources of this problem are typos in the makefile (if that filename is wrong) or a corrupted source tree (if that file is not supposed to be built, but rather only a prerequisite). 

Are you running 

```
make
```

From within the source directory ?

[COLOR="Red"]**Just ran "make" from within "i7z-0.26" directory on my non i7 laptop & it worked perfectly.**[/COLOR]

---

### Post by sclagler on 2010-11-01
greetings!


now decluttered

will follow your instructions later tonight...no time right now


thanks,
 - sheldon

---

### Post by gmargo on 2010-11-01
> 
sheldon@ubuntu:~/Desktop/i7z-0.26$ sudo make -d -r /Makefile
You are running make incorrectly.

Assuming you already have the **libncurses5-dev** package installed, here is the entire build procedure:

```

$ wget http://i7z.googlecode.com/files/i7z-0.26.tar.gz
$ tar xzf i7z-0.26.tar.gz
$ cd i7z-0.26/
$ make

```Then you need sudo to run it:
```

$ sudo ./i7z

```(BTW, do us all a favor and edit that post to cut down the reams of debug output.)

---

### Post by IcarusR on 2010-11-01
There is something very basic going wrong here ! But can not find it !

gmargo

> You are running make incorrectly.

That is what I said but OP says he is running from within source directory.

> Assuming you already have the libncurses5-dev package installed

Must have it installed other wise make will bug out complianing about lack of it as it did on my box before I installed libncurses5-dev.

It is VERY strange as I managed to run make successfuly on my non i7 laptop with no problems.

---

### Post by gmargo on 2010-11-01
> **IcarusR said:**
> It is VERY strange as I managed to run make successfuly on my non i7 laptop with no problems.
I don't think it's strange at all; you compiled a program.  Run the binary and see what it says.

---

### Post by sclagler on 2010-11-02
greetings!

Thanks to IcarusR and gmargo for your replies.

I was able to make the i7z and i7z_GUI binaries following gmargo's instructions.

I am also happy to report that the i7z installation went well.

I am embarrassed to report that the i7z_GUI installation didn't go as I'd like.

I used checkinstall and it shows up in synaptic as installed but I can only seem to run the program from the make binary location.  I can't find it anywhere else on my system.

I am also embarrassed to report that I can't seem to figure out how to read my cpu core temperature.

thanks again,
  -sheldon

---

