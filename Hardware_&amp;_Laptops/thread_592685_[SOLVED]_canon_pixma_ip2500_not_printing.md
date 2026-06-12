---
title: "[SOLVED] canon pixma ip2500 not printing"
date: 2007-10-26
forum: Hardware &amp; Laptops
---

### Post by genekrupa on 2007-10-26
Following this German wiki, [http://wiki.ubuntuusers.de/Canon-Drucker]("http://wiki.ubuntuusers.de/Canon-Drucker"), 
I managed to install the linux drivers provided by canon.  According to the testing procedures given there, the install is good.
However, the printer does not react on sending a testpage.
On further search, I found a manual , [www.manualnguide.com/download/manual-guide/canon-bj-pixma-ip2500-linux-print-filter-guide.html]("www.manualnguide.com/download/manual-guide/canon-bj-pixma-ip2500-linux-print-filter-guide.html")apparently from canon describing a final step for installing the printer. Unfortunately it is specified for fedora: 

"Register the printer to the spooler by using the lpadmin command from the command line of the terminal software. You can specify the desired name as the [printer_name].

/usr/sbin/lpadmin -p [printer_name] -m [PPD_filename] -v [device_URI] -E
If you specify IP2500 as the [printer_name]:
[root@zzz /yyy]# /usr/sbin/lpadmin -p IP2500 -m canonip2500.ppd -v cnij_usb:/dev/usb/lp0 -E"

Now I am stuck. I cannot figure out the right destination to copy the ppd-file to ( -v cnij_usb:blabla)   in ubuntu. The ubuntu-equivalent for /dev/usb/ in fedora seems to be /dev/**bus**/usb/. There, I do not find lp0, but a choice between /001, /002 and a file called devices. Which one do I have to choose? O do I have to create a folder/file called lp0?

Help appreciated.

---

### Post by froy02 on 2007-10-26
See if you can configure your printer by using firefox browser. Open it and type "http://localhost:631".  If printer dialog box opens up you can configure it there.

---

### Post by genekrupa on 2007-10-28
Thanks! 
There, the error message reads
"Filter "pstocanonij" for printer "iP2500" not available: No such file or directory". I followed the wiki mentioned above and installed a package to resolve the dependency. 

The install seems to have gone well. But the error message does not go away (and the printer doesn't work).  I wonder if this has to do with the order in which things were installed, and I will do a reinstall of all related packages starting with this one.

Unless someone has a better suggestion?

---

### Post by genekrupa on 2007-10-28
It works!

With synaptic, I installed
[I]bjfilter-2.5
bjfilter-2.6
libcnbj-2.5
libcnbj-2.6
pstocanonbj[/I]  (Not sure how much of this is necessary, though)

[I]libxml1
libglade0 
libpng3
libtiff4 [/I] 

From this page[http://www.canon-asia.com/index.jsp?fuseaction=support]("http://www.canon-asia.com/index.jsp?fuseaction=support")
I downloaded
*cnijfilter-common-2.70-2.src.rpm* AND
[I]cnijfilter-common-2.70-1.i386.rpm
cnijfilter-ip2500series-2.70-1.i386.rpm[/I]

I converted the packages from rpm to deb with alien.

I installed the debian versions of 
[I]cnijfilter-common-2.70-2.src.rpm
cnijfilter-ip2500series-2.70-1.i386.rpm[/I]

Now, I had all I needed except the file pstocanonij, which is either lacking in the  common-2.70-2 package or was corrupted by alien.  WHICH WAS THE PROBLEM!

From 
*cnijfilter-common-2.70-1.i386.rpm*, I extracted
the file *pstocanonij* and moved it to its right place:

[I]sudo mv ./pstocanonij /usr/lib/cups/filter/pstocanonij
sudo chown root:root /usr/lib/cups/filter/pstocanonij
sudo chmod u+x /usr/lib/cups/filter/pstocanonij[/I]

(as described in [http://www.ubuntu-forum.de/artikel/21912/Howto-bitte-verschieben-Canon-IP4300.html](http://www.ubuntu-forum.de/artikel/21912/Howto-bitte-verschieben-Canon-IP4300.html))

then I checked whether the DLLs were linked correctly
by doing
*/usr/local/bin$ ldd cifip2500*

(as described in the wiki mentioned in the first post of this thread. 
If the driver supplied by canon expects an older version of dll, 
the output from ldd cifip2500 will read something like
*libtiff.so.3 => not found*)

In my case, the only one change I had to do was: 

*/usr/lib$ sudo ln -s libtiff.so.4 libtiff.so.3*

Note that you have to move between directories /usr/local/bin and /usr/lib in the process.
I did a restart to update cups and connected and turned on the printer

Then I opened [http://localhost:631](http://localhost:631) and followed the 'add printer'- routine,  accepting all default  choices. I was guided right through (sometimes having to wait surprisingly long) to the page [http://localhost:631/printers](http://localhost:631/printers), from where I sent the test page. 

Quite easy once you know what to do!

---

### Post by Giltine238 on 2008-01-24
> **genekrupa said:**
> 
then I checked whether the DLLs were linked correctly
by doing
*/usr/local/bin$ ldd cip2500*


Ok, I'm stuck. There's no cip2500 in /usr/local/bin/, the printer installs fine (meaning there are no errors), I can send a test page, but the printer just sits there doing nothing. :confused:

My installation procedure:
Download the three rpm's, convert via alien, install, copy the pstocanonij file, restart CUPS, turn on/install printer.

Will load Windows to see if it works there (wish me luck, I haven't used it for a year now (thanks Linux))
[Edit] It works under windows

[Second edit] It works after linking libtiff.so.3 to libtiff.so.4

---

### Post by genekrupa on 2008-02-02
Sorry, the file name in usr/local/bin is [SIZE="4"]cifip2500[/SIZE], not cip2500.

---

### Post by skintythe1andonly on 2008-05-31
Hi

I am relatively new to Ubuntu and am still having problems installing my canon pixma ip2500.

when you get to checking the DLL's are working correctly you ran ldd cifip2500

I am a little confused as to what to do with the output. What do I link the files not found from this output to. there seems to be a lot missing

skint@skint-laptop:/usr/local/bin$ ldd cifip2500
	linux-gate.so.1 =>  (0xb7f0f000)
	libcnbpcmcm311.so => not found
	libcnbpess311.so => not found
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7ed8000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7ed4000)
	libtiff.so.3 => not found
	libpng.so.3 => not found
	libcnbpcnclapi311.so => not found
	libcnbpcnclbjcmd311.so => not found
	libcnbpcnclui311.so => not found
	libpopt.so.0 => /lib/libpopt.so.0 (0xb7ecb000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d7c000)
	/lib/ld-linux.so.2 (0xb7f10000)

I have downloaded the rpm's from the canon site. In have extracted them and installed them using alien. I have moved the pstocanonij file as instructed but am unsure what to do with the above.

Please help

---

### Post by skintythe1andonly on 2008-06-02
I finally got that working. I was missing the packages from synapic package manager of which i didnt have the repositories. I got them by adding

[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu) to sources.list

Thanks

---

### Post by Giltine238 on 2008-06-10
I ran into the same problems as skintythe1andonly with a fresh install of Ubuntu Hardy. No additional repositories are necessary, just make sure you convert your rpm's with the '--scripts' option, and link those missing libraries (they are installed, but not found):
```
cd /usr/lib
sudo ln -s libtiff.so.4 libtiff.so.3
sudo ln -s libcnbpcmcm311.so.6.50.1 libcnbpcmcm311.so
sudo ln -s libcnbpess311.so.3.0.9 libcnbpess311.so
sudo ln -s libcnbpcnclapi311.so.3.3.0 libcnbpcnclapi311.so
sudo ln -s libcnbpcnclbjcmd311.so.3.3.0 libcnbpcnclbjcmd311.so
sudo ln -s libcnbpcnclui311.so.3.3.0 libcnbpcnclui311.so
```

did the job in my case.

---

