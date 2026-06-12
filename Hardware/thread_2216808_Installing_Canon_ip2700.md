---
title: "Installing Canon ip2700"
date: 2014-04-14
forum: Hardware
---

### Post by salmichaels on 2014-04-14
Running 13.04. Originally I plugged it in and added it through "printers" and it found everything it needed on its own, and worked famously. I just reinstalled and when I do the same, add it thru printers, it crashes me out. 

So I dl the drivers directly from Canon, tried to install them using ./install.sh and I get: 

```
An error occurred. The package management system cannot be identified.
```

I firmly believe this printer can work, because I've had it working before!

---

### Post by salmichaels on 2014-04-15
[COLOR=#000000]I need to revive this thread. Here's an update. 

On the advise of someone who kindly helped out, I did this: 

```
cd Downloads/cnijfilter-ip2700series-3.30-1-i386-deb/packages
sudo dpkg -i cnijfilter-common_3.30-1_i386.deb 
sudo dpkg -i cnijfilter-ip2700series_3.30-1_i386.deb
```

Then, output on that was: 

```
 (Reading database ... 164857 files and directories currently installed.)
Preparing to replace cnijfilter-ip2700series 3.30-1 (using cnijfilter-ip2700series_3.30-1_i386.deb) ...
Unpacking replacement cnijfilter-ip2700series ...
dpkg: dependency problems prevent configuration of cnijfilter-ip2700series:
 cnijfilter-ip2700series depends on libtiff4; however:
  Package libtiff4 is not installed.

dpkg: error processing cnijfilter-ip2700series (--install):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 cnijfilter-ip2700series 
```

So, I did this
```
sudo apt-get install libtiff4
```

which seemed to work, and then entered 

```
 sudo dpkg -i cnijfilter-ip2700series_3.30-1_i386.deb 
```

again, and got:

[CODE](Reading database ... 164866 files and directories currently installed.)
Preparing to replace cnijfilter-ip2700series 3.30-1 (using cnijfilter-ip2700series_3.30-1_i386.deb) ...
Unpacking replacement cnijfilter-ip2700series ...
Setting up cnijfilter-ip2700series (3.30-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place[/CODE[/COLOR][COLOR=#000000]]

At this point I'm not really sure what to do. When I first installed 13.04 [/COLOR][COLOR=#000000]and plugged the printer in, I didn't have to do any command line. I opened printers, and it installed on its own, and was spitting out printed pages within 5 min. After a wipe and resinstall, printers just locked up when trying to install it. After doing all of the above I try to install it and printers just closes, and the printer remains uninstalled. 

That's where I'm at now. 

Thanks![/COLOR][COLOR=#FF0000]
[/COLOR][COLOR=#000000]
[/COLOR]

---

### Post by pdc on 2014-04-16
sorry; missed your PM; here is a post;

a couple of ways to look and see what sort of printer install has taken place: try clicking on this link; [http://localhost:631/printers/](http://localhost:631/printers/)         ........is the ip2700 registered there?

If you copy the command system-config-printer and then paste it into the screen you get when you press Alt and F2 together ......that opens a GUI box and that ..shows what is there and allows you to add 

If you don't have this tiny programme system-config-printer installed, the sudo apt-get install system-config-printer should deliver it

if you check what drivers are installed ...if you paste > dpkg -l | grep cnijfilter and paste back what you get .........hopefully you got your drivers installed;

_________________________--

oh dear; when I google on "Processing triggers for libc-bin ... ldconfig deferred processing now taking place"

I get such things as this [http://askubuntu.com/questions/54851/package-operation-failed-when-installing-software](http://askubuntu.com/questions/54851/package-operation-failed-when-installing-software)

---

### Post by salmichaels on 2014-04-16
You, are, a GENIUS! Thank you very much. It worked. I have printed pages in front of me, and I am ecstatic beyond words!

---

### Post by pdc on 2014-04-16
well done; enjoy

(Oh, and with thread tools, you can edit the title so it says: SOLVED ............... it will help any others; best wishes)

---

### Post by salmichaels on 2014-04-16
Okay - it wouldn't let me edit the Title, so i'm posting this - hope it works!

---

