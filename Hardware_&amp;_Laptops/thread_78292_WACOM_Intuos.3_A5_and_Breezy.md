---
title: "WACOM Intuos.3 A5 and Breezy"
date: 2005-10-18
forum: Hardware &amp; Laptops
---

### Post by kxs on 2005-10-18
I don`t have Breezy installed at the moment so it`s a question, not the problem with hardware yet.
Does Intuos.3 tablet work with Breezy out of the box? Or will I have to compile kernel or do more scary stuff?

---

### Post by kxs on 2005-10-18
OK, I`ve got Breezy installed now. My Intuos.3 tablet works but very very poor. It was better with Hoary where it worked much better without installing anything.
What to do with Breezy? I know that there`s Howto at LinuxWacom but it`s quite complicated and I don`t know if I should do all that things? Should I compile kernel or there are all the drivers already in Breezy`s kernel? Should I only edit the xorg.conf?

Edit:
OK, it works. I only had to edit xorg.conf just like in this post:
[http://ubuntuforums.org/showthread.php?t=25151]("http://ubuntuforums.org/showthread.php?t=25151")

---

### Post by kxs on 2005-10-19
:confused: The tablet worked really great, but after a while it stoped working at all. What to do???

---

### Post by kxs on 2005-10-19
OK, it works again. Strange, but at first it worked with event3 and now it`s event2.

Last question: how to enable Express Keys?

---

### Post by kxs on 2005-10-20
OK, I`ve founded something:
[http://web.telia.com/~u46133770/wacom/index.html]("http://web.telia.com/~u46133770/wacom/index.html")
unfortunately, I get error after "make" (./configure is OK)

```
krzysiek@linux:~/Desktop/wacom/expresskeys-0.2.4$ make
make  all-recursive
make[1]: Wej&#347;cie do katalogu `/home/krzysiek/Desktop/wacom/expresskeys-0.2.4'
Making all in src-expresskeys
make[2]: Wej&#347;cie do katalogu `/home/krzysiek/Desktop/wacom/expresskeys-0.2.4/src-expresskeys'
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -Wall -g -O2 -MT main_setup.o -MD -MP -MF ".deps/main_setup.Tpo" -c -o main_setup.o main_setup.c; \
then mv -f ".deps/main_setup.Tpo" ".deps/main_setup.Po"; else rm -f ".deps/main_setup.Tpo"; exit 1; fi
In file included from main_setup.c:21:
globals.h:42:35: error: X11/extensions/XInput.h: Nie ma takiego pliku ani katalogu
globals.h:43:34: error: X11/extensions/XTest.h: Nie ma takiego pliku ani katalogu
In file included from main_setup.c:21:
globals.h:99: error: syntax error before &#8216;*&#8217; token
globals.h:99: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;pad_info_block&#8217;globals.h:99: warning: data definition has no type or storage class
globals.h:100: error: syntax error before &#8216;*&#8217; token
globals.h:100: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;pen_info_block&#8217;
globals.h:100: warning: data definition has no type or storage class
globals.h:101: error: syntax error before &#8216;*&#8217; token
globals.h:101: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;pad_info&#8217;
globals.h:101: warning: data definition has no type or storage class
globals.h:102: error: syntax error before &#8216;*&#8217; token
globals.h:102: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;pen_info&#8217;
globals.h:102: warning: data definition has no type or storage class
globals.h:103: error: syntax error before &#8216;*&#8217; token
globals.h:103: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;pad_device&#8217;
globals.h:103: warning: data definition has no type or storage class
globals.h:104: error: syntax error before &#8216;*&#8217; token
globals.h:104: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;pen_device&#8217;
globals.h:104: warning: data definition has no type or storage class
globals.h:111: error: syntax error before &#8216;XDeviceInfo&#8217;
globals.h:112: error: syntax error before &#8216;XDeviceInfo&#8217;
main_setup.c: In function &#8216;main&#8217;:
main_setup.c:133: warning: implicit declaration of function &#8216;XTestQueryExtension&#8217;
main_setup.c:140: error: &#8216;XExtensionVersion&#8217; undeclared (first use in this function)
main_setup.c:140: error: (Each undeclared identifier is reported only once
main_setup.c:140: error: for each function it appears in.)
main_setup.c:140: error: &#8216;xinputext&#8217; undeclared (first use in this function)
main_setup.c:141: warning: implicit declaration of function &#8216;XGetExtensionVersion&#8217;
main_setup.c:141: error: &#8216;INAME&#8217; undeclared (first use in this function)
main_setup.c:142: error: syntax error before &#8216;)&#8217; token
main_setup.c:219: error: &#8216;Relative&#8217; undeclared (first use in this function)
make[2]: *** [main_setup.o] B&#322;&#261;d 1
make[2]: Opuszczenie katalogu `/home/krzysiek/Desktop/wacom/expresskeys-0.2.4/src-expresskeys'
make[1]: *** [all-recursive] B&#322;&#261;d 1
make[1]: Opuszczenie katalogu `/home/krzysiek/Desktop/wacom/expresskeys-0.2.4'
make: *** [all] B&#322;&#261;d 2
krzysiek@linux:~/Desktop/wacom/expresskeys-0.2.4$

```

please help :(

p.s. few things in polish there:
"Blad" means "Error"
"Opuszczenie katalogu" = "Leaving directory"
"Wejscie do katalogu" = Entering directory"

p.s.2 or maybe there is another way to run express keys on Intuos under ubuntu?

---

### Post by kxs on 2005-10-20
I`ve managed to go further (had to install libxi-dev package), but now I get this after "make":
```
krzysiek@linux:~/Desktop/wacom/expresskeys-0.2.4$ make
make  all-recursive
make[1]: Wej&#347;cie do katalogu `/home/krzysiek/Desktop/wacom/expresskeys-0.2.4'
Making all in src-expresskeys
make[2]: Wej&#347;cie do katalogu `/home/krzysiek/Desktop/wacom/expresskeys-0.2.4/src-expresskeys'
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -Wall -g -O2 -MT main_setup.o -MD -MP -MF ".deps/main_setup.Tpo" -c -o main_setup.o main_setup.c; \
then mv -f ".deps/main_setup.Tpo" ".deps/main_setup.Po"; else rm -f ".deps/main_setup.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -Wall -g -O2 -MT globals.o -MD -MP -MF ".deps/globals.Tpo" -c -o globals.o globals.c; \
then mv -f ".deps/globals.Tpo" ".deps/globals.Po"; else rm -f ".deps/globals.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -Wall -g -O2 -MT config_read.o -MD -MP -MF ".deps/config_read.Tpo" -c -o config_read.o config_read.c; \
then mv -f ".deps/config_read.Tpo" ".deps/config_read.Po"; else rm -f ".deps/config_read.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -Wall -g -O2 -MT config_write.o -MD -MP -MF ".deps/config_write.Tpo" -c -o config_write.o config_write.c; \
then mv -f ".deps/config_write.Tpo" ".deps/config_write.Po"; else rm -f ".deps/config_write.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -Wall -g -O2 -MT event_loop.o -MD -MP -MF ".deps/event_loop.Tpo" -c -o event_loop.o event_loop.c; \
then mv -f ".deps/event_loop.Tpo" ".deps/event_loop.Po"; else rm -f ".deps/event_loop.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -Wall -g -O2 -MT exec_shell.o -MD -MP -MF ".deps/exec_shell.Tpo" -c -o exec_shell.o exec_shell.c; \
then mv -f ".deps/exec_shell.Tpo" ".deps/exec_shell.Po"; else rm -f ".deps/exec_shell.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -Wall -g -O2 -MT get_device.o -MD -MP -MF ".deps/get_device.Tpo" -c -o get_device.o get_device.c; \
then mv -f ".deps/get_device.Tpo" ".deps/get_device.Po"; else rm -f ".deps/get_device.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -Wall -g -O2 -MT on_error.o -MD -MP -MF ".deps/on_error.Tpo" -c -o on_error.o on_error.c; \
then mv -f ".deps/on_error.Tpo" ".deps/on_error.Po"; else rm -f ".deps/on_error.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -Wall -g -O2 -MT on_signal.o -MD -MP -MF ".deps/on_signal.Tpo" -c -o on_signal.o on_signal.c; \
then mv -f ".deps/on_signal.Tpo" ".deps/on_signal.Po"; else rm -f ".deps/on_signal.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -Wall -g -O2 -MT pen_mode.o -MD -MP -MF ".deps/pen_mode.Tpo" -c -o pen_mode.o pen_mode.c; \
then mv -f ".deps/pen_mode.Tpo" ".deps/pen_mode.Po"; else rm -f ".deps/pen_mode.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I..    -Wall -g -O2 -MT reg_events.o -MD -MP -MF ".deps/reg_events.Tpo" -c -o reg_events.o reg_events.c; \
then mv -f ".deps/reg_events.Tpo" ".deps/reg_events.Po"; else rm -f ".deps/reg_events.Tpo"; exit 1; fi
gcc -Wall -g -O2   -o expresskeys -L/usr/X11R6/lib -lX11 -lXi -lXtst main_setup.o globals.o config_read.o config_write.o event_loop.o exec_shell.o get_device.o on_error.o on_signal.o pen_mode.o reg_events.o
/usr/bin/ld: cannot find -lXtst
collect2: ld returned 1 exit status
make[2]: *** [expresskeys] B&#322;&#261;d 1
make[2]: Opuszczenie katalogu `/home/krzysiek/Desktop/wacom/expresskeys-0.2.4/src-expresskeys'
make[1]: *** [all-recursive] B&#322;&#261;d 1
make[1]: Opuszczenie katalogu `/home/krzysiek/Desktop/wacom/expresskeys-0.2.4'
make: *** [all] B&#322;&#261;d 2
krzysiek@linux:~/Desktop/wacom/expresskeys-0.2.4$
```

---

### Post by kxs on 2005-10-20
OK, solved this also. I had to install libxtst-dev package (man, it was hard to find the right package).
So, I`ve built expresskeys package. Now another problem. How to use it? :rolleyes: 

When I run:
```
expresskeys pad stylus
```

I get:
```
expresskeys ERROR: Can not find pad device: pad
```

What to do??? Anyone?

---

### Post by kxs on 2005-10-23
:) My tablet works now with express keys. 
If someone has the same problem as I wrote before you must do this:
- from this site:
[http://linuxwacom.sourceforge.net/index.php/dl]("http://linuxwacom.sourceforge.net/index.php/dl") you must download the newer linux wacom package; in my case it was linuxwacom-0.7.0-1.tar.bz2
- in the terminal type:
```
locate wacom_drv.o
```

- you should get something like this:
```
/usr/X11R6/lib/modules/input/wacom_drv.o
```

- backup the old driver:
```
cp /usr/X11R6/lib/modules/input/wacom_drv.o /home/user/Desktop/wacom/wacom_drv.o_old
```

- now unpack the package: linuxwacom-0.7.0-1.tar.bz2 (you don`t need to compile anything)

- in the package`s folder enter "prebuilt"

- now replace with wacom_drv.o_xorg the older driver:
```
cp wacom_drv.o_xorg /usr/X11R6/lib/modules/input/wacom_drv.o
```

- now just restart X and it`s all done

Now you can use this program:
[http://web.telia.com/~u46133770/wacom/index.html]("http://web.telia.com/~u46133770/wacom/index.html")
and make your custom shortcuts to Express Keys :)

---

### Post by lisux on 2005-10-24
Hi kxs for your info about wacom tablets in ubuntu.
At the moment i'am trying to setup a graphire 2 tabler in ubuntu 5.10 .
I have tried using the wacom Xorg driver that comes with ubuntu and with the driver from the last linuxwacom release 0.7.0-1.
With both i have the same problem, sometimes the pencil cat;t go to some parts of the screen, it is like sometimes the tablet is confused with the screen resolution and uses another one, for example, sometimes i can go to the top of the screen, the tabler doesn't recognize the whole screen.
When this occurs, after 4 or 10 seconds the tablet works again correctly.
Any clues ...
Have you, or somebody, have the same problem.
There are any news from the ubuntu team about to imrpove the support for wacom tablets?
Thanks

---

### Post by kxs on 2005-11-11
Mine works fine.
Are you sure you`ve got your tablet configured to work in absolute mode?
```
Option "Mode" "absolute"
```

Also, try maybe searching linuxwacom mailing list:
[HTML]http://sourceforge.net/mailarchive/forum.php?forum_id=19621[/HTML]
Maybe you`ll find something usefull.

---

### Post by 23meg on 2005-11-11
Lisux, you probably need to adjust the Bottom/Top values of your tablet configuration to match your screen. Refer to the linuxwacom documentation on their website for instructions on how to do this.

---

### Post by kxs on 2005-11-11
Hmm... I think that Threshold option doesn`t work with my tablet. Or maybe I don`t get what should it do? It suppose to block actions when pressing value is lighter than Threshold number, yes?

---

### Post by 23meg on 2005-11-11
Quoting the linuxwacom documentation:
> 
               Option "Threshold" "number"
                   sets  the  pressure  threshold  used to generate a button 1
                   events of stylus. The default is MaxPressure*3/50.

---

### Post by kxs on 2005-11-11
OK. It works. But, unfortunately it doesn`t solve my problem:
I have a problem with GIMP. When drawing the cursor sometimes freezes. I`ve found similar problem at wacom-europe forum. As a salotiun someone wrote:
> In case you experience delays at when painting, please try to decrease the Tip Double Click Distance in the control panel.
I tried to decrease mouse double click at System-Preferences-Mouse, but that didn`t do the trick. I thought that maybe Threshold is a solution to this but it isn`t. So, what`s the problem? The GIMP or the wacom driver? What to do with that?

---

### Post by 23meg on 2005-11-11
Are you using dual monitors? If so I faintly recall there's a GIMP mode that you can activate using xsetwacom. "xsetwacom list param" should give you the details.

Does this happen only when GIMP is running? Did you play with the input device options in GIMP?

---

### Post by kxs on 2005-11-11
I`m using one monitor.
The problem is only with GIMP. Cursor freezes only sometimes when drawing. In other situations it works really great. Whit pressure turned off it is also OK. But I use pressure all the time and the corsor`s freezing becomes quite annoying when sketching.

---

### Post by 23meg on 2005-11-11
It probably has something to do with the input settings in GIMP then. Did you try alternating your devices between the "Screen" and "Window" modes in input settings?

---

### Post by kxs on 2005-11-11
the tablet works in screen mode as it better fits my needs.
and beside that, the cursor freezes sometimes in both modes.
if you want to reproduce the cursor freezing I`m talking about try to draw something in GIMP right after quick doubleclick (with pen tip of course)

here`s the link to similar subject on wacom-europe I was thalking about earlier:
[http://www.wacom-europe.com/forum/topic.asp?TOPIC_ID=3671]("http://www.wacom-europe.com/forum/topic.asp?TOPIC_ID=3671")
look at the end of that post.
maybe you know how to change doubleclick speed on wacom tablet? maybe I should change it in a diferent way than System-Preference-Mouse-doubleclick.

---

### Post by fktt on 2007-08-07
hey kxs i was wondering if you have tryed to get the express keys to work on feisty, and if so how easy/hard was it? (i havent yet tried to get em to work but would love to have em working[and it would be darn sweet to get the scroll on this pad to work too!])

---

### Post by mallow on 2007-09-29
> **fktt said:**
> hey kxs i was wondering if you have tryed to get the express keys to work on feisty, and if so how easy/hard was it? (i havent yet tried to get em to work but would love to have em working[and it would be darn sweet to get the scroll on this pad to work too!])

hi
It`s kxs here, only my new login is mallow.
My Intuos tablet works really good under feisty. To be honest I don`t remember if it just worked after upgrade to feisty or did I installed it the same way as under breezy. Now I wait for the Gutsy Gibbon release, as it`s coming soon and then try to write new HowTo: Intuos under ubuntu.
In general, Intuos with all the express keys and touch strips works really well, but the installation process could be easier. What I miss is a graphical tool to set everything up. What a shame that I`m no coder and can`t help with that out.

---

