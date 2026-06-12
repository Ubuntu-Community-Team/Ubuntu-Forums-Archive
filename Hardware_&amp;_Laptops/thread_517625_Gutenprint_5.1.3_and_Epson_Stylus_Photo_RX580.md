---
title: "Gutenprint 5.1.3 and Epson Stylus Photo RX580"
date: 2007-08-04
forum: Hardware &amp; Laptops
---

### Post by joncrlsn on 2007-08-04
I was stupid enough to purchase the (not so new) Epson Stylus Photo RX580 before checking to see if it was supported by Ubuntu (Kubuntu Feisty, actually)

t looks like in order to use this printer I have to compile Gutenprint 5.1.3 (Actually 5.1.1 or later).   Does that sound right?

I'm comfortable with downloading the source and doing these things:
./configure
make clean
make 
make install

Is there more that I need to do after that to get KDE to recognize the new libraries, etc?  

I really appreciate any help or suggestions.

- Jon

---

### Post by pbcartwright on 2007-08-04
first, I have an EpsonStylus Color 880, and it works fine with Linux. I also have an Epson 4180 Photo Scanner that didn't used to work with Linux. Epson is way behind with Linux drivers. Just hang in there , and it will work.
second, instead of make install, you might want to run checkinstall. It adds the application to the database, so if you ever want to install updates,  it will recognoze them..
installing your own apps is nice, but the database doesn't recognize them.

---

### Post by joncrlsn on 2007-08-04
> **pbcartwright said:**
> 
second, instead of make install, you might want to run checkinstall. It adds the application to the database, so if you ever want to install updates,  it will recognoze them..
installing your own apps is nice, but the database doesn't recognize them.

Thanks! 

This is what I did:
  1) Installed Gutenprint 5.1.3 (Some more RX model printers showed up after this, but not the RX580)
  2) Downloaded pipslite RPM from [www.avasys.jp/english](www.avasys.jp/english) and converted to debian with alien.  The avasys documentation says this file supports the Stylus Photo RX580
  3) Installed pipslite with 'sudo dpkg --install pipslite-1.0.0-1.deb'
  4) Restarted Linux to restart CUPS.
  
Still no RX580 showing up when I try to add a printer.  Is there possibly something else I need to do?

---

### Post by tistria on 2007-08-26
I have the same problem.  I've installed gutenprint (well, gimp-print), but still no driver in cups.  I want to install the pipslite package, but I'm running 64bit Feisty, and alien won't convert the RPM.  I tried compiling the source file from [http://www.avasys.jp/english/linux_e/dl_spc.html]("http://www.avasys.jp/english/linux_e/dl_spc.html"), but it returns several errors.

```
getstat.c:34:18: error: ltdl.h: No such file or directory
getstat.c: In function ‘str_extract’:
getstat.c:88: warning: cast from pointer to integer of different size
getstat.c:88: warning: cast from pointer to integer of different size
getstat.c: In function ‘get_printer_peculiar’:
getstat.c:141: error: ‘lt_dlhandle’ undeclared (first use in this function)
getstat.c:141: error: (Each undeclared identifier is reported only once
getstat.c:141: error: for each function it appears in.)
getstat.c:141: error: expected ‘;’ before ‘lib_h’
getstat.c:147: warning: implicit declaration of function ‘lt_dlinit’
getstat.c:150: warning: implicit declaration of function ‘lt_dlerror’
getstat.c:150: warning: passing argument 2 of ‘fprintf’ makes pointer from integer without a cast
getstat.c:153: error: ‘lib_h’ undeclared (first use in this function)
getstat.c:153: warning: implicit declaration of function ‘lt_dlopenext’
getstat.c:155: warning: passing argument 2 of ‘fprintf’ makes pointer from integer without a cast
getstat.c:159: warning: implicit declaration of function ‘lt_dlsym’
getstat.c:159: warning: cast to pointer from integer of different size
make[2]: *** [getstat.o] Error 1
make[2]: Leaving directory `/home/tim/packages/epson/pipslite-1.0.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tim/packages/epson/pipslite-1.0.0'
make: *** [all-recursive-am] Error 2
```

I'm at loss for what to do.

---

### Post by darenw on 2007-08-27
tistria,

>> getstat.c:34:18: error: ltdl.h: No such file or directory
>> ...gobs of more errors....

see if you have a package named libltdl3-dev installed.  it provides ltdl.h which would make that and the following errors vanish.

---

### Post by loadedmind on 2007-12-06
Hi folks.  When you  have a moment, might you please post a follow-up to the previous suggestion?  I'm about to perform a major switch and have a list of things that I'm trying to ensure will work before-hand.  I'm completely fed up with Winderz and have a SwitchView (Cybex now named Avocent) to switch between Fedora 7, Ubuntu Server and XP Pro.  The only reason I've been holding onto XP Pro is MS Flight Simulator & Counterstrike.  I've recently found viable alternatives for these programs but the sticking point for me is Epson RX580 support on Ubuntu.  So far, I haven't seen too many success stories so I'm kind of holding out.

Thanks!
LoadedMind

---

### Post by tistria on 2007-12-08
After much wailing and gnashing of teeth (and several other problems), I downgraded to 7.06 32 bit.  I have Pipslite installed, and according to the readme, I am supposed to run pipslite-install with the printer plugged into the computer.  But it just returns a dialog that says:

[INDENT]"PPD fIle need to be created for the printer to be registered to CUPS.  Please make sure that the printer is connected to your computer and have it turned on." (sic)[/INDENT]

It is plugged in directly via USB, and is on.  I actually intend to use it via a hardware printer server, but I figured I could make the PPD file via USB, and then use that file for the CUPS print server config.

---

