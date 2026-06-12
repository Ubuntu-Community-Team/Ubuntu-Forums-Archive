---
title: "Google Earth 5 in Intrepid"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by bhishan on 2009-02-10
I installed Google Earth 5 in my computer. When it try to run it it initializes and shuts down automatically. Need help.

---

### Post by Partyboi2 on 2009-02-10
Maybe starting it from the terminal might give some info into your problem. Open a terminal and start google earth with
```
googleearth
```

---

### Post by bhishan on 2009-02-10
I got this warning message when I tried to start it from the terminal.

Warning: Unable to create prefs directory '/home/bhishan/.googleearth'. File exists.
./googleearth-bin: relocation error: /usr/lib/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference

---

### Post by jastonas on 2009-02-10
maybe try running
sudo googleearth

---

### Post by icp on 2009-02-10
You must change the name of "libcrypto.so.0.9.8" whit:
```
mv /home/USER/google-earth/libcrypto.so.0.9.8 /home/USER/google-earth/libcrypto.so.0.9.8bug
``` :)

---

### Post by jastonas on 2009-02-10
i tried rename and wouldnt work not even with sudo. I just renamed it with nautilus and now google earth works fine. Thanks for the solution.

---

### Post by bhishan on 2009-02-11
thanks, renaming with nautilus worked for me too. Google earth opened but the graphics is all fu**** up. The version is 5.0.11337.1968 (beta). Is there any way to fix it.Is it because it is beta version?

---

### Post by icp on 2009-02-12
I don't know why, but my GoogleEarth works fine with only rename libcrypto.

---

### Post by bhishan on 2009-02-14
Didnt work on mine. I uninstalled it.

---

### Post by johnjohn2 on 2009-02-14
Perfect worked like a charm

---

### Post by Harksaw on 2009-02-14
> **icp said:**
> You must change the name of "libcrypto.so.0.9.8" whit:
```
mv /home/USER/google-earth/libcrypto.so.0.9.8 /home/USER/google-earth/libcrypto.so.0.9.8bug
``` :)

Thanks, this worked.

---

### Post by sopier on 2009-02-15
I installed Google Earth 5.0 in Hardy, everything is Ok except Google Earth 5.0 feels like so slow compared to 4.3 version.

---

### Post by silentb on 2009-02-18
It feels like GE v5 doesn't utilize hardware acceleration.

---

### Post by harshguy on 2009-02-22
I have a problem. I got the prgram working but now the words in google earth are getting cut off. So, a date such as Feb 1998 is coming up as:
Fe  998. Some letters are missing. How can this be fixed

---

### Post by Altin on 2009-02-28
Worked great for me in Hardy. Changed name to libcrypto.so.0.9.8REMOVE_ME, and Google Earth starts without crashing.

---

### Post by mossgrove on 2009-03-01
I also cannot get this to work - graphics all foulded up and dead slow.  Ubuntu 8.10 on Intel D930 with 2GB memory and Intel 82G33/G31 graphics.  On install I get :

loki_setup: Suspect size value for option option

/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
loki_setup: Suspect size value for option option

Installing mimetypes...
Installing desktop menu entries...
Installing desktop icon...


Relative newbie to Linux (just got clean after 20years of MS indoctrination!)  Grateful for any help.

---

### Post by adonet on 2009-03-01
This is what I did:
Download the file and save it in your home directory. Open a terminal in the same directory.
Type in that terminal:
```
chmod + x. / GoogleEarthLinux.bin
```
to make the file executable
then type (still in the same directory from your terminal):
```
sudo ./GoogleEarthLinux.bin
```
and follow the installation (you can leave the defaults)

Then DON't start the program yet, but remove or rename the file
libcrypto.so.0.9.8
in
/opt/googleearth

so type in a terminal
```
gksu nautilus
```
hit enter and enter your password. Now you're having Nautilus with sudo rights and can delete files in /opt/googleearth.

When this is finished, Google Earth 5 beta will run.

---

### Post by user17 on 2009-03-02
> **adonet said:**
> 
```
chmod + x. / GoogleEarthLinux.bin
```
to make the file executable


@Adonet: Shouldn't this be **chmod a + x**? Oh well, I'm not really complaining, as your fix worked perfectly for me. Thanks.

---

### Post by adonet on 2009-03-03
> **user17 said:**
> @Adonet: Shouldn't this be **chmod a + x**? Oh well, I'm not really complaining, as your fix worked perfectly for me. Thanks.
It's possible that you're right. I combined some tips I found in several forums.

---

### Post by corpsehacker on 2009-04-09
It looks like you dont even have to use nautilus to rename or remove the file.

---

### Post by Yumi on 2009-04-10
Fix is not working here. Renaming libcrypto.so.0.9.8 does not solve the error. Removed GE completely until final.

Michael

---

### Post by ionraedt on 2009-04-12
I renamed libcrypto.so also and GE 5 starts up fine but now it is so slow that it doesn't succeed in building up the screen (screen is messed up with rectangular parts showing all possible colours and parts of the picture). I think it is a graphics problem (I have intel GMA X3100 with Ubuntu 8.1). I think there is something wrong with hardware acceleration. Anybody else having same problem ??

---

### Post by ionraedt on 2009-04-12
> **silentb said:**
> It feels like GE v5 doesn't utilize hardware acceleration.
I renamed <libcrypto.so> also and GE 5 starts up fine but now it is so slow that it doesn't succeed in building up the screen (screen is messed up with rectangular parts showing all possible colours and parts of the picture). I also think it is a graphics problem (I have intel GMA X3100 with Ubuntu 8.1). I think there is something wrong with hardware acceleration. Anybody else having same problem ??

---

### Post by adonet on 2009-04-14
> **ionraedt said:**
> I renamed <libcrypto.so> also and GE 5 starts up fine but now it is so slow that it doesn't succeed in building up the screen (screen is messed up with rectangular parts showing all possible colours and parts of the picture). I also think it is a graphics problem (I have intel GMA X3100 with Ubuntu 8.1). I think there is something wrong with hardware acceleration. Anybody else having same problem ??

Ubuntu 8.1? Do you mean 8.04.1? in that case you should run the update manager. 8.04.2 is the current LTS version.
Or do you mean 8.10 that's the current version.

GE (any version) needs 3d hardware accelleration. You could try to install stellarium from the repositories (use synaptic). If that works OK, the problem probably is in GE. If stellarium doesn't work either, tou've probably a hardware acceleration problem.
In that case I 'd do a google search with the words "ubuntu 'name of graphic card' hardware acc" or something like that, to see if someone got the card to work properly with ubuntu.

---

