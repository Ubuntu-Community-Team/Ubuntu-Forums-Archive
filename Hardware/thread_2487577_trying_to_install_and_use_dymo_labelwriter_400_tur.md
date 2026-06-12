---
title: "trying to install and use dymo labelwriter 400 turbo"
date: 2023-06-08
forum: Hardware
---

### Post by jgw on 2023-06-08
I am trying to install a dymo labelwriter 400 turbo.  I have it plugged in and recognized insettings.  The driver that I have installed is DYMO LabelMANAGER 400  Whilst it seems to be ready to go it is not printing.  I have, obviously, screwed up.  Oh, I am using Glabels to print.  I have read a number of things on the net.  I have followed what I found in [https://installati.one/install-printer-driver-dymo-ubuntu-22-04/](https://installati.one/install-printer-driver-dymo-ubuntu-22-04/)    I have also done what I found in: [https://ubuntu.pkgs.org/22.04/ubuntu-universe-amd64/printer-driver-dymo_1.4.0-11_amd64.deb.html](https://ubuntu.pkgs.org/22.04/ubuntu-universe-amd64/printer-driver-dymo_1.4.0-11_amd64.deb.html).  There was another place that told me to do some stuff with cups.  I am, obviously, flailing and figured it was really time to stop and ask somebody for help before things blow up.  

So far, nothing that I have tried as done anything to activate the printer so I think I remain ok.  I have also run tests to no avail.  My dymo 400 turbo is currently in my printer settings and is processing but doesn't have a job.  I have no idea what its processing but nothing is happening.  I am going to turn off the printer power and wait anybody's thoughts before I start back up on this one.  A plain test from settings also does nothing.  The only thing I can get it do is feet a label.

Thank you..............

---

### Post by #&amp;thj^% on 2023-06-08
@ jgw have a look here: [https://github.com/Kyle-Falconer/DYMO-SDK-for-Linux](https://github.com/Kyle-Falconer/DYMO-SDK-for-Linux)
As far as cups goes, we will have to see when your finished with the link.

---

### Post by jgw on 2023-06-08
Thankyou for the reply and help...

I forgot to mention that I have been running a dymo 400 for years, in ubuntu (at least 5 years) with no problems.  Then the printer died.  I wrote to dymo and talked to a support guy and I sent him pictures of the printer and the power supply and he wrote back and said the warrenty was waaay done and he had no idea why it was dead but there was nothing he could do.  Its been so long I don't even remember how I set it up.

This is where I'm at now with what you sent me:
greg@greg-HP-EliteBook-8560p:~$ git clone [https://github.com/Kyle-Falconer/DYMO-SDK-for-Linux.git](https://github.com/Kyle-Falconer/DYMO-SDK-for-Linux.git)
Cloning into 'DYMO-SDK-for-Linux'...
remote: Enumerating objects: 196, done.
remote: Total 196 (delta 0), reused 0 (delta 0), pack-reused 196
Receiving objects: 100% (196/196), 274.30 KiB | 576.00 KiB/s, done.
Resolving deltas: 100% (100/100), done.
greg@greg-HP-EliteBook-8560p:~$ cd DYMO-SDK-for-Linux
greg@greg-HP-EliteBook-8560p:~/DYMO-SDK-for-Linux$ aclocal
greg@greg-HP-EliteBook-8560p:~/DYMO-SDK-for-Linux$ Automake --add-missing
Command 'Automake' not found, did you mean:
  command 'automake' from deb automake (1:1.16.5-1.3)
  command 'automake' from deb automake1.11 (1:1.11.6-6)
Try: sudo apt install <deb name>

Before I went any further I thought I would ask if I should........

---

### Post by #&amp;thj^% on 2023-06-08
That appears strange to me (Automake and not automake?)
But no matter yes please do run it.
As far as using a Dymo for a spell, keep in mind things change quickly here. LOL
I wouldn't say it was ever easy to install for everyone. ;)

---

### Post by #&amp;thj^% on 2023-06-09
Yes I was right automake && not Automake. (You must of cap'ed the a)
If you ran into any missing packages please run:
```
sudo apt install cups-bsd 
sudo apt install lpr 
sudo apt install lprng 
```
BTW it installs just fine on Lunar 23.04

---

### Post by jgw on 2023-06-09
thank you for the help.

Here is what I did.  First I deleted any and all printers as I think we are starting over.  Then I pressed the add key and nothing happened.  Then I pressed the Additional printer settings and have sent a picture of the result.  So, currently I cannot enter any new settings because its got all my old settings (none of which work).  I went back to settings and they were all there.  I removed them all again and then clicked on the dymo printer.  The second picture is where I am now.  I should add that the driver for the dymo just appeared and location is empty and address is local host.  I also noticed something about attach below and hope its right and you can see the two photos I attached (in theory).  You can also see the result of your suggestion I do at [https://pastebin.com/095v9cmB](https://pastebin.com/095v9cmB)  (I lost the address that ubuntu uses for posting stuff) 

Its all very strange .  My regular printer no longer does anything as well as the dymo.  I have, I think, cleverly screwed it all up.  No errors no nuthin.............

[ATTACH=CONFIG]292365[/ATTACH]

---

### Post by #&amp;thj^% on 2023-06-09
Wow it blew up the printing world in your box.
This is crazy:
```
The following packages will be REMOVED:
  bluez-cups cups cups-client hplip lpr printer-driver-gutenprint
  printer-driver-hpcups printer-driver-splix
```
Not to mention:
```
cups-bsd is already the newest version (2.4.1op1-1ubuntu4.2).
cups-bsd set to manually installed.
```
Even more madness:
```
sudo apt install lpr 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Suggested packages:
  magicfilter | apsfilter
The following packages will be REMOVED:
  cups-bsd
The following NEW packages will be installed:
  lpr
```
Now I show on mine:
```
apt policy cups-bsd
cups-bsd:
  Installed: 2.4.2-3ubuntu3
  Candidate: 2.4.2-3ubuntu3
  Version table:
 *** 2.4.2-3ubuntu3 500
        500 http://archive.ubuntu.com/ubuntu devel/main amd64 Packages
        100 /var/lib/dpkg/status

```
Greg I would remove the "lpr" package and reinstall "cups-bsd"
EDIT:
```
apt policy printer-driver-dymo
printer-driver-dymo:
  Installed: 1.4.0-12
  Candidate: 1.4.0-12
  Version table:
 *** 1.4.0-12 500
        500 http://archive.ubuntu.com/ubuntu devel/universe amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by #&amp;thj^% on 2023-06-10
jgw I hope things are still good here and your not doing another re-install, there is no need for that unless other things are acting strangely.
You really did not need to "delete" any of the Printers you had installed, that link was a patch for cups* Dymo no longer supports Linux so some folks got busy
and add the needed code to fit the cups we have currently.
It builds just fine on both Debian/Ubuntu and based OS's, and I just compiled it for Arch as well:
See how cups dependent it was:
```
In file included from CupsFilterLabelWriter.h:26,
                 from CupsFilterLabelWriter.cpp:21:
/usr/include/cups/ppd.h:377:26: note: declared here
  377 | extern ppd_choice_t     *ppdFindMarkedChoice(ppd_file_t *ppd,
      |                          ^~~~~~~~~~~~~~~~~~~
CupsFilterLabelWriter.cpp:39:31: warning: &#8216;ppd_choice_t* ppdFindMarkedChoice(ppd_file_t*, const char*)&#8217; is deprecated: Use cupsCopyDestInfo and friends instead. [-Wdeprecated-declarations]
   39 |   choice = ppdFindMarkedChoice(ppd, "DymoPrintQuality");
      |            ~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~
/usr/include/cups/ppd.h:377:26: note: declared here
  377 | extern ppd_choice_t     *ppdFindMarkedChoice(ppd_file_t *ppd,
      |                          ^~~~~~~~~~~~~~~~~~~
CupsFilterLabelWriter.cpp:51:31: warning: &#8216;ppd_choice_t* ppdFindMarkedChoice(ppd_file_t*, const char*)&#8217; is deprecated: Use cupsCopyDestInfo and friends instead. [-Wdeprecated-declarations]
   51 |   choice = ppdFindMarkedChoice(ppd, "DymoPrintDensity");
      |            ~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~
/usr/include/cups/ppd.h:377:26: note: declared here
  377 | extern ppd_choice_t     *ppdFindMarkedChoice(ppd_file_t *ppd,
      |                          ^~~~~~~~~~~~~~~~~~~
CupsFilterLabelWriter.cpp: In static member function &#8216;static void DymoPrinterDriver::CDriverInitializerLabelWriterTwinTurbo::ProcessPPDOptions(DymoPrinterDriver::CLabelWriterDriverTwinTurbo&, DymoPrinterDriver::CDummyLanguageMonitor&, ppd_file_t*)&#8217;:
CupsFilterLabelWriter.cpp:103:45: warning: &#8216;ppd_choice_t* ppdFindMarkedChoice(ppd_file_t*, const char*)&#8217; is deprecated: Use cupsCopyDestInfo and friends instead. [-Wdeprecated-declarations]
  103 |   ppd_choice_t* choice = ppdFindMarkedChoice(ppd, "InputSlot");
      |                          ~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~
/usr/include/cups/ppd.h:377:26: note: declared here
  377 | extern ppd_choice_t     *ppdFindMarkedChoice(ppd_file_t *ppd,
      |                          ^~~~~~~~~~~~~~~~~~~
mv -f .deps/CupsFilterLabelWriter.Tpo .deps/CupsFilterLabelWriter.Po
g++ -DHAVE_CONFIG_H -I. -I../../src -I../common    -O2 -Wall -Wno-unknown-pragmas   -MT CupsPrintEnvironment.o -MD -MP -MF .deps/CupsPrintEnvironment.Tpo -c -o CupsPrintEnvironment.o `test -f '../common/CupsPrintEnvironment.cpp' || echo './'`../common/CupsPrintEnvironment.cpp
mv -f .deps/CupsPrintEnvironment.Tpo .deps/CupsPrintEnvironment.Po
g++ -DHAVE_CONFIG_H -I. -I../../src -I../common    -O2 -Wall -Wno-unknown-pragmas   -MT Halftoning.o -MD -MP -MF .deps/Halftoning.Tpo -c -o Halftoning.o `test -f '../common/Halftoning.cpp' || echo './'`../common/Halftoning.cpp
../common/Halftoning.cpp: In member function &#8216;int DymoPrinterDriver::CHalftoneFilter::ExtractRGB(const DymoPrinterDriver::buffer_t&, int)&#8217;:
../common/Halftoning.cpp:157:40: warning: &#8216;<<&#8217; in boolean context, did you mean &#8216;<&#8217;? [-Wint-in-bool-context]
  157 |         (int(InputLine[4*PixelNo + 1]) << 16)
      |         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~^~~~~~
../common/Halftoning.cpp:158:43: warning: &#8216;<<&#8217; in boolean context, did you mean &#8216;<&#8217;? [-Wint-in-bool-context]
  158 |         || (int(InputLine[4*PixelNo + 2]) << 8)
      |            ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~^~~~~
../common/Halftoning.cpp:162:40: warning: &#8216;<<&#8217; in boolean context, did you mean &#8216;<&#8217;? [-Wint-in-bool-context]
  162 |         (int(InputLine[3*PixelNo + 0]) << 16)
      |         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~^~~~~~
../common/Halftoning.cpp:163:43: warning: &#8216;<<&#8217; in boolean context, did you mean &#8216;<&#8217;? [-Wint-in-bool-context]
  163 |         || (int(InputLine[3*PixelNo + 1]) << 8)
      |            ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~^~~~~
mv -f .deps/Halftoning.Tpo .deps/Halftoning.Po
g++ -DHAVE_CONFIG_H -I. -I../../src -I../common    -O2 -Wall -Wno-unknown-pragmas   -MT ErrorDiffusionHalftoning.o -MD -MP -MF .deps/ErrorDiffusionHalftoning.Tpo -c -o ErrorDiffusionHalftoning.o `test -f '../common/ErrorDiffusionHalftoning.cpp' || echo './'`../common/ErrorDiffusionHalftoning.cpp
mv -f .deps/ErrorDiffusionHalftoning.Tpo .deps/ErrorDiffusionHalftoning.Po
g++ -DHAVE_CONFIG_H -I. -I../../src -I../common    -O2 -Wall -Wno-unknown-pragmas   -MT NonLinearLaplacianHalftoning.o -MD -MP -MF .deps/NonLinearLaplacianHalftoning.Tpo -c -o NonLinearLaplacianHalftoning.o `test -f '../common/NonLinearLaplacianHalftoning.cpp' || echo './'`../common/NonLinearLaplacianHalftoning.cpp
mv -f .deps/NonLinearLaplacianHalftoning.Tpo .deps/NonLinearLaplacianHalftoning.Po
g++ -DHAVE_CONFIG_H -I. -I../../src -I../common    -O2 -Wall -Wno-unknown-pragmas   -MT DummyLanguageMonitor.o -MD -MP -MF .deps/DummyLanguageMonitor.Tpo -c -o DummyLanguageMonitor.o `test -f '../common/DummyLanguageMonitor.cpp' || echo './'`../common/DummyLanguageMonitor.cpp
mv -f .deps/DummyLanguageMonitor.Tpo .deps/DummyLanguageMonitor.Po
g++  -O2 -Wall -Wno-unknown-pragmas    -Wl,-O1,--sort-common,--as-needed,-z,relro,-z,now -o raster2dymolw raster2dymolw.o LabelWriterDriver.o LabelWriterLanguageMonitor.o CupsFilterLabelWriter.o CupsPrintEnvironment.o Halftoning.o ErrorDiffusionHalftoning.o NonLinearLaplacianHalftoning.o DummyLanguageMonitor.o  -lcupsimage -lcups 
make[4]: Leaving directory '/home/me/.cache/yay/dymo-cups-drivers/src/dymo-cups-drivers-1.4.0.5/src/lw'
make[3]: Leaving directory '/home/me/.cache/yay/dymo-cups-drivers/src/dymo-cups-drivers-1.4.0.5/src/lw'
Making all in lm
make[3]: Entering directory '/home/me/.cache/yay/dymo-cups-drivers/src/dymo-cups-drivers-1.4.0.5/src/lm'
Making all in tests
make[4]: Entering directory '/home/me/.cache/yay/dymo-cups-drivers/src/dymo-cups-drivers-1.4.0.5/src/lm/tests'
make[4]: Nothing to be done for 'all'.
make[4]: Leaving directory '/home/me/.cache/yay/dymo-cups-drivers/src/dymo-cups-drivers-1.4.0.5/src/lm/tests'
make[4]: Entering directory '/home/me/.cache/yay/dymo-cups-drivers/src/dymo-cups-drivers-1.4.0.5/src/lm'
g++ -DHAVE_CONFIG_H -I. -I../../src -I../common    -O2 -Wall -Wno-unknown-pragmas   -MT raster2dymolm.o -MD -MP -MF .deps/raster2dymolm.Tpo -c -o raster2dymolm.o raster2dymolm.cpp
In file included from raster2dymolm.cpp:34:
../common/CupsFilter.h: In member function &#8216;int DymoPrinterDriver::CCupsFilter<D, DI, LM>::Run(int, char**)&#8217;:
../common/CupsFilter.h:136:10: warning: &#8216;template<class> class std::auto_ptr&#8217; is deprecated: use 'std::unique_ptr' instead [-Wdeprecated-declarations]
  136 |     std::auto_ptr<CHalftoneFilter> H;
      |          ^~~~~~~~
In file included from /usr/include/c++/13.1.1/memory:78,
                 from raster2dymolm.cpp:27:
/usr/include/c++/13.1.1/bits/unique_ptr.h:65:28: note: declared here
   65 |   template<typename> class auto_ptr;
      |                            ^~~~~~~~
../common/CupsFilter.h: In member function &#8216;void DymoPrinterDriver::CCupsFilter<D, DI, LM>::InitDocument(const char*)&#8217;:
../common/CupsFilter.h:219:32: warning: &#8216;ppd_file_t* ppdOpenFile(const char*)&#8217; is deprecated: Use cupsCopyDestInfo and friends instead. [-Wdeprecated-declarations]
  219 |   ppd_file_t* ppd = ppdOpenFile(getenv("PPD"));
      |                     ~~~~~~~~~~~^~~~~~~~~~~~~~~
In file included from ../common/CupsFilter.h:26:
/usr/include/cups/ppd.h:389:26: note: declared here
  389 | extern ppd_file_t       *ppdOpenFile(const char *filename) _CUPS_DEPRECATED_1_6_MSG("Use cupsCopyDestInfo and friends instead.");
      |                          ^~~~~~~~~~~
../common/CupsFilter.h:229:18: warning: &#8216;void ppdMarkDefaults(ppd_file_t*)&#8217; is deprecated: Use cupsCopyDestInfo and friends instead. [-Wdeprecated-declarations]
  229 |   ppdMarkDefaults(ppd);
      |   ~~~~~~~~~~~~~~~^~~~~
/usr/include/cups/ppd.h:384:25: note: declared here
  384 | extern void             ppdMarkDefaults(ppd_file_t *ppd) _CUPS_DEPRECATED_1_6_MSG("Use cupsCopyDestInfo and friends instead.");
      |                         ^~~~~~~~~~~~~~~
../common/CupsFilter.h:235:20: warning: &#8216;int ppdMarkOption(ppd_file_t*, const char*, const char*)&#8217; is deprecated: Use cupsCopyDestInfo and friends instead. [-Wdeprecated-declarations]
  235 |       ppdMarkOption(ppd, Options[i].name, Options[i].value);
      |       ~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/usr/include/cups/ppd.h:385:25: note: declared here
  385 | extern int              ppdMarkOption(ppd_file_t *ppd, const char *keyword,
      |                         ^~~~~~~~~~~~~
../common/CupsFilter.h:239:18: warning: &#8216;int cupsMarkOptions(ppd_file_t*, int, cups_option_t*)&#8217; is deprecated: Use cupsCopyDestInfo and friends instead. [-Wdeprecated-declarations]
  239 |   cupsMarkOptions(ppd, OptionCount, Options);
      |   ~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~
/usr/include/cups/ppd.h:362:25: note: declared here
  362 | extern int              cupsMarkOptions(ppd_file_t *ppd, int num_options, cups_option_t *options) _CUPS_DEPRECATED_1_6_MSG("Use cupsCopyDestInfo and friends instead.");
      |                         ^~~~~~~~~~~~~~~
../common/CupsFilter.h:244:45: warning: &#8216;ppd_choice_t* ppdFindMarkedChoice(ppd_file_t*, const char*)&#8217; is deprecated: Use cupsCopyDestInfo and friends instead. [-Wdeprecated-declarations]
  244 |   ppd_choice_t* choice = ppdFindMarkedChoice(ppd, "DymoHalftoning");
      |                          ~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~
/usr/include/cups/ppd.h:377:26: note: declared here
  377 | extern ppd_choice_t     *ppdFindMarkedChoice(ppd_file_t *ppd,
      |                          ^~~~~~~~~~~~~~~~~~~
../common/CupsFilter.h:249:11: warning: &#8216;void ppdClose(ppd_file_t*)&#8217; is deprecated: Use cupsCopyDestInfo and friends instead. [-Wdeprecated-declarations]
  249 |   ppdClose(ppd);
      |   ~~~~~~~~^~~~~
/usr/include/cups/ppd.h:364:25: note: declared here
  364 | extern void             ppdClose(ppd_file_t *ppd) _CUPS_DEPRECATED_1_6_MSG("Use cupsCopyDestInfo and friends instead.");
      |                         ^~~~~~~~
../common/CupsFilter.h: In instantiation of &#8216;void DymoPrinterDriver::CCupsFilter<D, DI, LM>::InitDocument(const char*) [with D = DymoPrinterDriver::CLabelManagerDriver; DI = DymoPrinterDriver::CDriverInitializerLabelManagerWithLM; LM = DymoPrinterDriver::CLabelManagerLanguageMonitor]&#8217;:
../common/CupsFilter.h:100:3:   required from &#8216;int DymoPrinterDriver::CCupsFilter<D, DI, LM>::Run(int, char**) [with D = DymoPrinterDriver::CLabelManagerDriver; DI = DymoPrinterDriver::CDriverInitializerLabelManagerWithLM; LM = DymoPrinterDriver::CLabelManagerLanguageMonitor]&#8217;
raster2dymolm.cpp:53:22:   required from here
../common/CupsFilter.h:219:32: warning: &#8216;ppd_file_t* ppdOpenFile(const char*)&#8217; is deprecated: Use cupsCopyDestInfo and friends instead. [-Wdeprecated-declarations]
  219 |   ppd_file_t* ppd = ppdOpenFile(getenv("PPD"));
      |                     ~~~~~~~~~~~^~~~~~~~~~~~~~~
/usr/include/cups/ppd.h:389:26: note: declared here
  389 | extern ppd_file_t       *ppdOpenFile(const char *filename) _CUPS_DEPRECATED_1_6_MSG("Use cupsCopyDestInfo and friends instead.");
      |                          ^~~~~~~~~~~
../common/CupsFilter.h:219:32: warning: &#8216;ppd_file_t* ppdOpenFile(const char*)&#8217; is deprecated: Use cupsCopyDestInfo and friends instead. [-Wdeprecated-declarations]
  219 |   ppd_file_t* ppd = ppdOpenFile(getenv("PPD"));
      |                     ~~~~~~~~~~~^~~~~~~~~~~~~~~
/usr/include/cups/ppd.h:389:26: note: declared here
  389 | extern ppd_file_t       *ppdOpenFile(const char *filename) _CUPS_DEPRECATED_1_6_MSG("Use cupsCopyDestInfo and friends instead.");
      |                          ^~~~~~~~~~~
../common/CupsFilter.h:229:18: warning: &#8216;void ppdMarkDefaults(ppd_file_t*)&#8217; is deprecated: Use cupsCopyDestInfo and friends instead. [-Wdeprecated-declarations]
  229 |   ppdMarkDefaults(ppd);
      |   ~~~~~~~~~~~~~~~^~~~~
/usr/include/cups/ppd.h:384:25: note: declared here
  384 | extern void             ppdMarkDefaults(ppd_file_t *ppd) _CUPS_DEPRECATED_1_6_MSG("Use cupsCopyDestInfo and friends instead.");
      |                         ^~~~~~~~~~~~~~~
../common/CupsFilter.h:229:18: warning: &#8216;void ppdMarkDefaults(ppd_file_t*)&#8217; is deprecated: Use cupsCopyDestInfo and friends instead. [-Wdeprecated-declarations]
  229 |   ppdMarkDefaults(ppd);
      |   ~~~~~~~~~~~~~~~^~~~~
/usr/include/cups/ppd.h:384:25: note: declared here
  384 | extern void             ppdMarkDefaults(ppd_file_t *ppd) _CUPS_DEPRECATED_1_6_MSG("Use cupsCopyDestInfo and friends instead.");
      |                         ^~~~~~~~~~~~~~~
../common/CupsFilter.h:235:20: warning: &#8216;int ppdMarkOption(ppd_file_t*, const char*, const char*)&#8217; is deprecated: Use cupsCopyDestInfo and friends instead. [-Wdeprecated-declarations]
  235 |       ppdMarkOption(ppd, Options[i].name, Options[i].value);
      |       ~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/usr/include/cups/ppd.h:385:25: note: declared here
  385 | extern int              ppdMarkOption(ppd_file_t *ppd, const char *keyword,
      |                         ^~~~~~~~~~~~~
../common/CupsFilter.h:235:20: warning: &#8216;int ppdMarkOption(ppd_file_t*, const char*, const char*)&#8217; is deprecated: Use cupsCopyDestInfo and friends instead. [-Wdeprecated-declarations]
  235 |       ppdMarkOption(ppd, Options[i].name, Options[i].value);
      |       ~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/usr/include/cups/ppd.h:385:25: note: declared here
  385 | extern int              ppdMarkOption(ppd_file_t *ppd, const char *keyword,
      |                         ^~~~~~~~~~~~~
../common/CupsFilter.h:239:18: warning: &#8216;int cupsMarkOptions(ppd_file_t*, int, cups_option_t*)&#8217; is deprecated: Use cupsCopyDestInfo and friends instead. [-Wdeprecated-declarations]
  239 |   cupsMarkOptions(ppd, OptionCount, Options);
      |   ~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~
/usr/include/cups/ppd.h:362:25: note: declared here
  362 | extern int              cupsMarkOptions(ppd_file_t *ppd, int num_options, cups_option_t *options) _CUPS_DEPRECATED_1_6_MSG("Use cupsCopyDestInfo and friends instead.");
      |                         ^~~~~~~~~~~~~~~
../common/CupsFilter.h:239:18: warning: &#8216;int cupsMarkOptions(ppd_file_t*, int, cups_option_t*)&#8217; is deprecated: Use cupsCopyDestInfo and friends instead. [-Wdeprecated-declarations]
  239 |   cupsMarkOptions(ppd, OptionCount, Options);
      |   ~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~
/usr/include/cups/ppd.h:362:25: note: declared here
  362 | extern int              cupsMarkOptions(ppd_file_t *ppd, int num_options, cups_option_t *options) _CUPS_DEPRECATED_1_6_MSG("Use cupsCopyDestInfo and friends instead.");
      |                         ^~~~~~~~~~~~~~~
../common/CupsFilter.h:244:45: warning: &#8216;ppd_choice_t* ppdFindMarkedChoice(ppd_file_t*, const char*)&#8217; is deprecated: Use cupsCopyDestInfo and friends instead. [-Wdeprecated-declarations]
  244 |   ppd_choice_t* choice = ppdFindMarkedChoice(ppd, "DymoHalftoning");
      |                          ~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~
/usr/include/cups/ppd.h:377:26: note: declared here
  377 | extern ppd_choice_t     *ppdFindMarkedChoice(ppd_file_t *ppd,
      |                          ^~~~~~~~~~~~~~~~~~~
../common/CupsFilter.h:244:45: warning: &#8216;ppd_choice_t* ppdFindMarkedChoice(ppd_file_t*, const char*)&#8217; is deprecated: Use cupsCopyDestInfo and friends instead. [-Wdeprecated-declarations]
  244 |   ppd_choice_t* choice = ppdFindMarkedChoice(ppd, "DymoHalftoning");
      |                          ~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~
/usr/include/cups/ppd.h:377:26: note: declared here
  377 | extern ppd_choice_t     *ppdFindMarkedChoice(ppd_file_t *ppd,
      |                          ^~~~~~~~~~~~~~~~~~~
../common/CupsFilter.h:249:11: warning: &#8216;void ppdClose(ppd_file_t*)&#8217; is deprecated: Use cupsCopyDestInfo and friends instead. [-Wdeprecated-declarations]
  249 |   ppdClose(ppd);
      |   ~~~~~~~~^~~~~
/usr/include/cups/ppd.h:364:25: note: declared here
  364 | extern void             ppdClose(ppd_file_t *ppd) _CUPS_DEPRECATED_1_6_MSG("Use cupsCopyDestInfo and friends instead.");
      |                         ^~~~~~~~
../common/CupsFilter.h:249:11: warning: &#8216;void ppdClose(ppd_file_t*)&#8217; is deprecated: Use cupsCopyDestInfo and friends instead. [-Wdeprecated-declarations]
  249 |   ppdClose(ppd);
      |   ~~~~~~~~^~~~~
/usr/include/cups/ppd.h:364:25: note: declared here
  364 | extern void             ppdClose(ppd_file_t *ppd) _CUPS_DEPRECATED_1_6_MSG("Use cupsCopyDestInfo and friends instead.");
      |                         ^~~~~~~~
../common/CupsFilter.h: In instantiation of &#8216;void DymoPrinterDriver::CCupsFilter<D, DI, LM>::InitDocument(const char*) [with D = DymoPrinterDriver::CLabelManagerDriver; DI = DymoPrinterDriver::CDriverInitializerLabelManager; LM = DymoPrinterDriver::CDummyLanguageMonitor]&#8217;:
../common/CupsFilter.h:100:3:   required from &#8216;int DymoPrinterDriver::CCupsFilter<D, DI, LM>::Run(int, char**) [with D = DymoPrinterDriver::CLabelManagerDriver; DI = DymoPrinterDriver::CDriverInitializerLabelManager; LM = DymoPrinterDriver::CDummyLanguageMonitor]&#8217;
raster2dymolm.cpp:58:22:   required from here
../common/CupsFilter.h:219:32: warning: &#8216;ppd_file_t* ppdOpenFile(const char*)&#8217; is deprecated: Use cupsCopyDestInfo and friends instead. [-Wdeprecated-declarations]
  219 |   ppd_file_t* ppd = ppdOpenFile(getenv("PPD"));
      |                     ~~~~~~~~~~~^~~~~~~~~~~~~~~
/usr/include/cups/ppd.h:389:26: note: declared here
  389 | extern ppd_file_t       *ppdOpenFile(const char *filename) _CUPS_DEPRECATED_1_6_MSG("Use cupsCopyDestInfo and friends instead.");
      |                          ^~~~~~~~~~~
../common/CupsFilter.h:219:32: warning: &#8216;ppd_file_t* ppdOpenFile(const char*)&#8217; is deprecated: Use cupsCopyDestInfo and friends instead. [-Wdeprecated-declarations]
  219 |   ppd_file_t* ppd = ppdOpenFile(getenv("PPD"));
      |                     ~~~~~~~~~~~^~~~~~~~~~~~~~~
/usr/include/cups/ppd.h:389:26: note: declared here
  389 | extern ppd_file_t       *ppdOpenFile(const char *filename) _CUPS_DEPRECATED_1_6_MSG("Use cupsCopyDestInfo and friends instead.");
      |                          ^~~~~~~~~~~
../common/CupsFilter.h:229:18: warning: &#8216;void ppdMarkDefaults(ppd_file_t*)&#8217; is deprecated: Use cupsCopyDestInfo and friends instead. [-Wdeprecated-declarations]
  229 |   ppdMarkDefaults(ppd);
      |   ~~~~~~~~~~~~~~~^~~~~
/usr/include/cups/ppd.h:384:25: note: declared here
  384 | extern void             ppdMarkDefaults(ppd_file_t *ppd) _CUPS_DEPRECATED_1_6_MSG("Use cupsCopyDestInfo and friends instead.");
      |                         ^~~~~~~~~~~~~~~
../common/CupsFilter.h:229:18: warning: &#8216;void ppdMarkDefaults(ppd_file_t*)&#8217; is deprecated: Use cupsCopyDestInfo and friends instead. [-Wdeprecated-declarations]
  229 |   ppdMarkDefaults(ppd);
      |   ~~~~~~~~~~~~~~~^~~~~
/usr/include/cups/ppd.h:384:25: note: declared here
  384 | extern void             ppdMarkDefaults(ppd_file_t *ppd) _CUPS_DEPRECATED_1_6_MSG("Use cupsCopyDestInfo and friends instead.");
      |                         ^~~~~~~~~~~~~~~
../common/CupsFilter.h:235:20: warning: &#8216;int ppdMarkOption(ppd_file_t*, const char*, const char*)&#8217; is deprecated: Use cupsCopyDestInfo and friends instead. [-Wdeprecated-declarations]
  235 |       ppdMarkOption(ppd, Options[i].name, Options[i].value);
      |       ~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/usr/include/cups/ppd.h:385:25: note: declared here
  385 | extern int              ppdMarkOption(ppd_file_t *ppd, const char *keyword,
      |                         ^~~~~~~~~~~~~
../common/CupsFilter.h:235:20: warning: &#8216;int ppdMarkOption(ppd_file_t*, const char*, const char*)&#8217; is deprecated: Use cupsCopyDestInfo and friends instead. [-Wdeprecated-declarations]
  235 |       ppdMarkOption(ppd, Options[i].name, Options[i].value);
      |       ~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/usr/include/cups/ppd.h:385:25: note: declared here
  385 | extern int              ppdMarkOption(ppd_file_t *ppd, const char *keyword,
      |                         ^~~~~~~~~~~~~
../common/CupsFilter.h:239:18: warning: &#8216;int cupsMarkOptions(ppd_file_t*, int, cups_option_t*)&#8217; is deprecated: Use cupsCopyDestInfo and friends instead. [-Wdeprecated-declarations]
  239 |   cupsMarkOptions(ppd, OptionCount, Options);
      |   ~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~
/usr/include/cups/ppd.h:362:25: note: declared here
  362 | extern int              cupsMarkOptions(ppd_file_t *ppd, int num_options, cups_option_t *options) _CUPS_DEPRECATED_1_6_MSG("Use cupsCopyDestInfo and friends instead.");
      |                         ^~~~~~~~~~~~~~~
../common/CupsFilter.h:239:18: warning: &#8216;int cupsMarkOptions(ppd_file_t*, int, cups_option_t*)&#8217; is deprecated: Use cupsCopyDestInfo and friends instead. [-Wdeprecated-declarations]
  239 |   cupsMarkOptions(ppd, OptionCount, Options);
      |   ~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~
/usr/include/cups/ppd.h:362:25: note: declared here
  362 | extern int              cupsMarkOptions(ppd_file_t *ppd, int num_options, cups_option_t *options) _CUPS_DEPRECATED_1_6_MSG("Use cupsCopyDestInfo and friends instead.");
      |                         ^~~~~~~~~~~~~~~
../common/CupsFilter.h:244:45: warning: &#8216;ppd_choice_t* ppdFindMarkedChoice(ppd_file_t*, const char*)&#8217; is deprecated: Use cupsCopyDestInfo and friends instead. [-Wdeprecated-declarations]
  244 |   ppd_choice_t* choice = ppdFindMarkedChoice(ppd, "DymoHalftoning");
      |                          ~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~
/usr/include/cups/ppd.h:377:26: note: declared here
  377 | extern ppd_choice_t     *ppdFindMarkedChoice(ppd_file_t *ppd,
      |                          ^~~~~~~~~~~~~~~~~~~
../common/CupsFilter.h:244:45: warning: &#8216;ppd_choice_t* ppdFindMarkedChoice(ppd_file_t*, const char*)&#8217; is deprecated: Use cupsCopyDestInfo and friends instead. [-Wdeprecated-declarations]
  244 |   ppd_choice_t* choice = ppdFindMarkedChoice(ppd, "DymoHalftoning");
      |                          ~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~
/usr/include/cups/ppd.h:377:26: note: declared here
  377 | extern ppd_choice_t     *ppdFindMarkedChoice(ppd_file_t *ppd,
      |                          ^~~~~~~~~~~~~~~~~~~
../common/CupsFilter.h:249:11: warning: &#8216;void ppdClose(ppd_file_t*)&#8217; is deprecated: Use cupsCopyDestInfo and friends instead. [-Wdeprecated-declarations]
  249 |   ppdClose(ppd);
      |   ~~~~~~~~^~~~~
/usr/include/cups/ppd.h:364:25: note: declared here
  364 | extern void             ppdClose(ppd_file_t *ppd) _CUPS_DEPRECATED_1_6_MSG("Use cupsCopyDestInfo and friends instead.");
      |                         ^~~~~~~~
../common/CupsFilter.h:249:11: warning: &#8216;void ppdClose(ppd_file_t*)&#8217; is deprecated: Use cupsCopyDestInfo and friends instead. [-Wdeprecated-declarations]
  249 |   ppdClose(ppd);
      |   ~~~~~~~~^~~~~
/usr/include/cups/ppd.h:364:25: note: declared here
  364 | extern void             ppdClose(ppd_file_t *ppd) _CUPS_DEPRECATED_1_6_MSG("Use cupsCopyDestInfo and friends instead.");
      |                         ^~~~~~~~
mv -f .deps/raster2dymolm.Tpo .deps/raster2dymolm.Po
g++ -DHAVE_CONFIG_H -I. -I../../src -I../common    -O2 -Wall -Wno-unknown-pragmas   -MT LabelManagerDriver.o -MD -MP -MF .deps/LabelManagerDriver.Tpo -c -o LabelManagerDriver.o LabelManagerDriver.cpp
mv -f .deps/LabelManagerDriver.Tpo .deps/LabelManagerDriver.Po
g++ -DHAVE_CONFIG_H -I. -I../../src -I../common    -O2 -Wall -Wno-unknown-pragmas   -MT CupsFilterLabelManager.o -MD -MP -MF .deps/CupsFilterLabelManager.Tpo -c -o CupsFilterLabelManager.o CupsFilterLabelManager.cpp
CupsFilterLabelManager.cpp: In static member function &#8216;static void DymoPrinterDriver::CDriverInitializerLabelManager::ProcessPPDOptions(DymoPrinterDriver::CLabelManagerDriver&, DymoPrinterDriver::CDummyLanguageMonitor&, ppd_file_t*)&#8217;:
CupsFilterLabelManager.cpp:29:45: warning: &#8216;ppd_choice_t* ppdFindMarkedChoice(ppd_file_t*, const char*)&#8217; is deprecated: Use cupsCopyDestInfo and friends instead. [-Wdeprecated-declarations]
   29 |   ppd_choice_t* choice = ppdFindMarkedChoice(ppd, "DymoCutOptions");
      |                          ~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~
In file included from CupsFilterLabelManager.h:26,
                 from CupsFilterLabelManager.cpp:21:
/usr/include/cups/ppd.h:377:26: note: declared here
  377 | extern ppd_choice_t     *ppdFindMarkedChoice(ppd_file_t *ppd,
      |                          ^~~~~~~~~~~~~~~~~~~
CupsFilterLabelManager.cpp:41:31: warning: &#8216;ppd_choice_t* ppdFindMarkedChoice(ppd_file_t*, const char*)&#8217; is deprecated: Use cupsCopyDestInfo and friends instead. [-Wdeprecated-declarations]
   41 |   choice = ppdFindMarkedChoice(ppd, "DymoLabelAlignment");
      |            ~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~
/usr/include/cups/ppd.h:377:26: note: declared here
  377 | extern ppd_choice_t     *ppdFindMarkedChoice(ppd_file_t *ppd,
      |                          ^~~~~~~~~~~~~~~~~~~
CupsFilterLabelManager.cpp:56:31: warning: &#8216;ppd_choice_t* ppdFindMarkedChoice(ppd_file_t*, const char*)&#8217; is deprecated: Use cupsCopyDestInfo and friends instead. [-Wdeprecated-declarations]
   56 |   choice = ppdFindMarkedChoice(ppd, "DymoPrintChainMarksAtDocEnd");
      |            ~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/usr/include/cups/ppd.h:377:26: note: declared here
  377 | extern ppd_choice_t     *ppdFindMarkedChoice(ppd_file_t *ppd,
      |                          ^~~~~~~~~~~~~~~~~~~
CupsFilterLabelManager.cpp:64:31: warning: &#8216;ppd_choice_t* ppdFindMarkedChoice(ppd_file_t*, const char*)&#8217; is deprecated: Use cupsCopyDestInfo and friends instead. [-Wdeprecated-declarations]
   64 |   choice = ppdFindMarkedChoice(ppd, "DymoContinuousPaper");
      |            ~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~
/usr/include/cups/ppd.h:377:26: note: declared here
  377 | extern ppd_choice_t     *ppdFindMarkedChoice(ppd_file_t *ppd,
      |                          ^~~~~~~~~~~~~~~~~~~
CupsFilterLabelManager.cpp:72:31: warning: &#8216;ppd_choice_t* ppdFindMarkedChoice(ppd_file_t*, const char*)&#8217; is deprecated: Use cupsCopyDestInfo and friends instead. [-Wdeprecated-declarations]
   72 |   choice = ppdFindMarkedChoice(ppd, "DymoTapeColor");
      |            ~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~
/usr/include/cups/ppd.h:377:26: note: declared here
  377 | extern ppd_choice_t     *ppdFindMarkedChoice(ppd_file_t *ppd,
      |                          ^~~~~~~~~~~~~~~~~~~
mv -f .deps/CupsFilterLabelManager.Tpo .deps/CupsFilterLabelManager.Po
g++ -DHAVE_CONFIG_H -I. -I../../src -I../common    -O2 -Wall -Wno-unknown-pragmas   -MT LabelManagerLanguageMonitor.o -MD -MP -MF .deps/LabelManagerLanguageMonitor.Tpo -c -o LabelManagerLanguageMonitor.o LabelManagerLanguageMonitor.cpp
mv -f .deps/LabelManagerLanguageMonitor.Tpo .deps/LabelManagerLanguageMonitor.Po
g++ -DHAVE_CONFIG_H -I. -I../../src -I../common    -O2 -Wall -Wno-unknown-pragmas   -MT CupsPrintEnvironment.o -MD -MP -MF .deps/CupsPrintEnvironment.Tpo -c -o CupsPrintEnvironment.o `test -f '../common/CupsPrintEnvironment.cpp' || echo './'`../common/CupsPrintEnvironment.cpp
mv -f .deps/CupsPrintEnvironment.Tpo .deps/CupsPrintEnvironment.Po
g++ -DHAVE_CONFIG_H -I. -I../../src -I../common    -O2 -Wall -Wno-unknown-pragmas   -MT Halftoning.o -MD -MP -MF .deps/Halftoning.Tpo -c -o Halftoning.o `test -f '../common/Halftoning.cpp' || echo './'`../common/Halftoning.cpp
../common/Halftoning.cpp: In member function &#8216;int DymoPrinterDriver::CHalftoneFilter::ExtractRGB(const DymoPrinterDriver::buffer_t&, int)&#8217;:
../common/Halftoning.cpp:157:40: warning: &#8216;<<&#8217; in boolean context, did you mean &#8216;<&#8217;? [-Wint-in-bool-context]
  157 |         (int(InputLine[4*PixelNo + 1]) << 16)
      |         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~^~~~~~
../common/Halftoning.cpp:158:43: warning: &#8216;<<&#8217; in boolean context, did you mean &#8216;<&#8217;? [-Wint-in-bool-context]
  158 |         || (int(InputLine[4*PixelNo + 2]) << 8)
      |            ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~^~~~~
../common/Halftoning.cpp:162:40: warning: &#8216;<<&#8217; in boolean context, did you mean &#8216;<&#8217;? [-Wint-in-bool-context]
  162 |         (int(InputLine[3*PixelNo + 0]) << 16)
      |         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~^~~~~~
../common/Halftoning.cpp:163:43: warning: &#8216;<<&#8217; in boolean context, did you mean &#8216;<&#8217;? [-Wint-in-bool-context]
  163 |         || (int(InputLine[3*PixelNo + 1]) << 8)
      |            ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~^~~~~
mv -f .deps/Halftoning.Tpo .deps/Halftoning.Po
g++ -DHAVE_CONFIG_H -I. -I../../src -I../common    -O2 -Wall -Wno-unknown-pragmas   -MT ErrorDiffusionHalftoning.o -MD -MP -MF .deps/ErrorDiffusionHalftoning.Tpo -c -o ErrorDiffusionHalftoning.o `test -f '../common/ErrorDiffusionHalftoning.cpp' || echo './'`../common/ErrorDiffusionHalftoning.cpp
mv -f .deps/ErrorDiffusionHalftoning.Tpo .deps/ErrorDiffusionHalftoning.Po
g++ -DHAVE_CONFIG_H -I. -I../../src -I../common    -O2 -Wall -Wno-unknown-pragmas   -MT NonLinearLaplacianHalftoning.o -MD -MP -MF .deps/NonLinearLaplacianHalftoning.Tpo -c -o NonLinearLaplacianHalftoning.o `test -f '../common/NonLinearLaplacianHalftoning.cpp' || echo './'`../common/NonLinearLaplacianHalftoning.cpp
mv -f .deps/NonLinearLaplacianHalftoning.Tpo .deps/NonLinearLaplacianHalftoning.Po
g++ -DHAVE_CONFIG_H -I. -I../../src -I../common    -O2 -Wall -Wno-unknown-pragmas   -MT DummyLanguageMonitor.o -MD -MP -MF .deps/DummyLanguageMonitor.Tpo -c -o DummyLanguageMonitor.o `test -f '../common/DummyLanguageMonitor.cpp' || echo './'`../common/DummyLanguageMonitor.cpp
mv -f .deps/DummyLanguageMonitor.Tpo .deps/DummyLanguageMonitor.Po
g++  -O2 -Wall -Wno-unknown-pragmas    -Wl,-O1,--sort-common,--as-needed,-z,relro,-z,now -o raster2dymolm raster2dymolm.o LabelManagerDriver.o CupsFilterLabelManager.o LabelManagerLanguageMonitor.o CupsPrintEnvironment.o Halftoning.o ErrorDiffusionHalftoning.o NonLinearLaplacianHalftoning.o DummyLanguageMonitor.o  -lcupsimage -lcups 
make[4]: Leaving directory '/home/me/.cache/yay/dymo-cups-drivers/src/dymo-cups-drivers-1.4.0.5/src/lm'
make[3]: Leaving directory '/home/me/.cache/yay/dymo-cups-drivers/src/dymo-cups-drivers-1.4.0.5/src/lm'
Making all in common/tests
make[3]: Entering directory '/home/me/.cache/yay/dymo-cups-drivers/src/dymo-cups-drivers-1.4.0.5/src/common/tests'
make[3]: Nothing to be done for 'all'.
make[3]: Leaving directory '/home/me/.cache/yay/dymo-cups-drivers/src/dymo-cups-drivers-1.4.0.5/src/common/tests'
make[3]: Entering directory '/home/me/.cache/yay/dymo-cups-drivers/src/dymo-cups-drivers-1.4.0.5/src'
make[3]: Leaving directory '/home/me/.cache/yay/dymo-cups-drivers/src/dymo-cups-drivers-1.4.0.5/src'
make[2]: Leaving directory '/home/me/.cache/yay/dymo-cups-drivers/src/dymo-cups-drivers-1.4.0.5/src'
make[1]: Leaving directory '/home/me/.cache/yay/dymo-cups-drivers/src/dymo-cups-drivers-1.4.0.5/src'
Making all in ppd
make[1]: Entering directory '/home/me/.cache/yay/dymo-cups-drivers/src/dymo-cups-drivers-1.4.0.5/ppd'
make[1]: Nothing to be done for 'all'.
make[1]: Leaving directory '/home/me/.cache/yay/dymo-cups-drivers/src/dymo-cups-drivers-1.4.0.5/ppd'
Making all in docs
make[1]: Entering directory '/home/me/.cache/yay/dymo-cups-drivers/src/dymo-cups-drivers-1.4.0.5/docs'
make[1]: Nothing to be done for 'all'.
make[1]: Leaving directory '/home/me/.cache/yay/dymo-cups-drivers/src/dymo-cups-drivers-1.4.0.5/docs'
Making all in samples
make[1]: Entering directory '/home/me/.cache/yay/dymo-cups-drivers/src/dymo-cups-drivers-1.4.0.5/samples'
Making all in paper_bounds
make[2]: Entering directory '/home/me/.cache/yay/dymo-cups-drivers/src/dymo-cups-drivers-1.4.0.5/samples/paper_bounds'
make[2]: Nothing to be done for 'all'.
make[2]: Leaving directory '/home/me/.cache/yay/dymo-cups-drivers/src/dymo-cups-drivers-1.4.0.5/samples/paper_bounds'
Making all in paper_list
make[2]: Entering directory '/home/me/.cache/yay/dymo-cups-drivers/src/dymo-cups-drivers-1.4.0.5/samples/paper_list'
make[2]: Nothing to be done for 'all'.
make[2]: Leaving directory '/home/me/.cache/yay/dymo-cups-drivers/src/dymo-cups-drivers-1.4.0.5/samples/paper_list'
Making all in test_label
make[2]: Entering directory '/home/me/.cache/yay/dymo-cups-drivers/src/dymo-cups-drivers-1.4.0.5/samples/test_label'
make[2]: Nothing to be done for 'all'.
make[2]: Leaving directory '/home/me/.cache/yay/dymo-cups-drivers/src/dymo-cups-drivers-1.4.0.5/samples/test_label'
Making all in custom_paper
make[2]: Entering directory '/home/me/.cache/yay/dymo-cups-drivers/src/dymo-cups-drivers-1.4.0.5/samples/custom_paper'
make[2]: Nothing to be done for 'all'.
make[2]: Leaving directory '/home/me/.cache/yay/dymo-cups-drivers/src/dymo-cups-drivers-1.4.0.5/samples/custom_paper'
Making all in custom_paper_tape
make[2]: Entering directory '/home/me/.cache/yay/dymo-cups-drivers/src/dymo-cups-drivers-1.4.0.5/samples/custom_paper_tape'
make[2]: Nothing to be done for 'all'.
make[2]: Leaving directory '/home/me/.cache/yay/dymo-cups-drivers/src/dymo-cups-drivers-1.4.0.5/samples/custom_paper_tape'
make[2]: Entering directory '/home/me/.cache/yay/dymo-cups-drivers/src/dymo-cups-drivers-1.4.0.5/samples'
make[2]: Nothing to be done for 'all-am'.
make[2]: Leaving directory '/home/me/.cache/yay/dymo-cups-drivers/src/dymo-cups-drivers-1.4.0.5/samples'
make[1]: Leaving directory '/home/me/.cache/yay/dymo-cups-drivers/src/dymo-cups-drivers-1.4.0.5/samples'
make[1]: Entering directory '/home/me/.cache/yay/dymo-cups-drivers/src/dymo-cups-drivers-1.4.0.5'
make[1]: Nothing to be done for 'all-am'.
make[1]: Leaving directory '/home/me/.cache/yay/dymo-cups-drivers/src/dymo-cups-drivers-1.4.0.5'
==> Entering fakeroot environment...

```
and the same version is used:
```
pacman -Qi dymo-cups-drivers
Name            : dymo-cups-drivers
Version         : 1.4.0.5-5
Description     : Official Dymo supplied Linux Cups drivers for LabelWriter
                  series
Architecture    : x86_64
URL             : http://global.dymo.com/
Licenses        : GPL  LGPL
Groups          : None
Provides        : None
Depends On      : libcups
Optional Deps   : None
Required By     : None
Optional For    : None
Conflicts With  : None
Replaces        : None
Installed Size  : 1069.04 KiB
Packager        : Unknown Packager
Build Date      : Sat 10 Jun 2023 04:02:18 PM MDT
Install Date    : Sat 10 Jun 2023 04:02:41 PM MDT
Install Reason  : Explicitly installed
Install Script  : No
Validated By    : None

```

---

### Post by jgw on 2023-06-10
On reflection I think I screwed up (again).  For some strange reason I thought that the:
printer-driver-dymo:
  Installed: 1.4.0-11
  Candidate: 1.4.0-11
etc. 
deleted the lpr package so I didn't do that.  I also thought I had sent you the address of what I did do.  If I didn't its here:
 [https://pastebin.com/JrHJZRtY](https://pastebin.com/JrHJZRtY)

I will now Just leave everything until I hear from you again (if you can - I'm a bit embarrassed.  I really am trying to pay attention. 
My current system printer place says: 'the system printing service is not available and shows me no printers.  I have actually screwed things up.  I have no idea what I have done.  printer is blank.   I think my wife's printer should show and also my dymo 400 turbo.  Its got its light on so its got power and it is plugged into my computer but the "add printer" button is also greyed out.

I suspect the first thing I have to do is to get settings to recognize ANYTHING!   just checked my usb connection and have: Dymo-CoStar Corp. LabelWriter 400 Turbo

---

### Post by #&amp;thj^% on 2023-06-10
Yes I seen the link, where do you think I got all that info in post #7?
And this is never a good sign>>>"the "add printer" button is also greyed out."

Kind Sir there is absolutely NO reason to feel  embarrassed, I think it safe to say we as in everyone has a moment or two that we wish we could turn back time on.
Hell I screw up all the time, I learn and push forward, relearn and still push forward. (It's just who I am)

---

### Post by #&amp;thj^% on 2023-06-11
if still no printers lets first remove the patch:
Let's see if we can get you straight now:
```
cd DYMO-SDK-for-Linux
sudo make uninstall
```
See if your other printers work now, you may have to re-install them first.
let me know how things are please.

---

### Post by jgw on 2023-06-11
something happened!

The last part of your request didn't work:

greg@greg-HP-EliteBook-8560p:~/DYMO-SDK-for-Linux$ sudo make uninstall
[sudo] password for greg: 
make: *** No rule to make target 'uninstall'.  Stop.

I sent the above Then I think I got something from you but not sure as its not on this site (last time I looked)

Anyway, I am now stopped.

---

### Post by #&amp;thj^% on 2023-06-12
> **jgw said:**
> something happened!

The last part of your request didn't work:

greg@greg-HP-EliteBook-8560p:~/DYMO-SDK-for-Linux$ sudo make uninstall
[sudo] password for greg: 
make: *** No rule to make target 'uninstall'.  Stop.

I sent the above Then I think I got something from you but not sure as its not on this site (last time I looked)

Anyway, I am now stopped.

jgw, please show all I ask first:
```
cd ~/ && ls
```
mine:
```
Desktop    Downloads           Music     Public     temp.file  Videos
Documents  DYMO-SDK-for-Linux  Pictures  rtl8812au  Templates

```
I just need to know we are on the same page.
Now run:
```
cd DYMO-SDK-for-Linux && ls
```
mine:
```
aclocal.m4      configure               install-sh     NEWS
AUTHORS         configure.ac            LICENSE        ppd
autom4te.cache  COPYING                 Makefile       README.md
ChangeLog       depcomp                 Makefile.am    samples
compile         docs                    Makefile.in    src
config.log      dymo-cups-drivers.spec  missing        test-driver
config.status   INSTALL                 mkinstalldirs

```
Now again run 
```
sudo make uninstall
```
Should run like below:
```
DYMO-SDK-for-Linux 
&#9492;&#9472;> sudo make uninstall
[sudo] password for me: 
Making uninstall in src
make[1]: Entering directory '/home/me/DYMO-SDK-for-Linux/src'
Making uninstall in lw
make[2]: Entering directory '/home/me/DYMO-SDK-for-Linux/src/lw'
Making uninstall in tests
make[3]: Entering directory '/home/me/DYMO-SDK-for-Linux/src/lw/tests'
make[3]: Nothing to be done for 'uninstall'.
make[3]: Leaving directory '/home/me/DYMO-SDK-for-Linux/src/lw/tests'
make[3]: Entering directory '/home/me/DYMO-SDK-for-Linux/src/lw'
 ( cd '/usr/lib/cups/filter' && rm -f raster2dymolw )
make[3]: Leaving directory '/home/me/DYMO-SDK-for-Linux/src/lw'
make[2]: Leaving directory '/home/me/DYMO-SDK-for-Linux/src/lw'
Making uninstall in lm
make[2]: Entering directory '/home/me/DYMO-SDK-for-Linux/src/lm'
Making uninstall in tests
make[3]: Entering directory '/home/me/DYMO-SDK-for-Linux/src/lm/tests'
make[3]: Nothing to be done for 'uninstall'.
make[3]: Leaving directory '/home/me/DYMO-SDK-for-Linux/src/lm/tests'
make[3]: Entering directory '/home/me/DYMO-SDK-for-Linux/src/lm'
 ( cd '/usr/lib/cups/filter' && rm -f raster2dymolm )
make[3]: Leaving directory '/home/me/DYMO-SDK-for-Linux/src/lm'
make[2]: Leaving directory '/home/me/DYMO-SDK-for-Linux/src/lm'
Making uninstall in common/tests
make[2]: Entering directory '/home/me/DYMO-SDK-for-Linux/src/common/tests'
make[2]: Nothing to be done for 'uninstall'.
make[2]: Leaving directory '/home/me/DYMO-SDK-for-Linux/src/common/tests'
make[2]: Entering directory '/home/me/DYMO-SDK-for-Linux/src'
make[2]: Nothing to be done for 'uninstall-am'.
make[2]: Leaving directory '/home/me/DYMO-SDK-for-Linux/src'
make[1]: Leaving directory '/home/me/DYMO-SDK-for-Linux/src'
Making uninstall in ppd
make[1]: Entering directory '/home/me/DYMO-SDK-for-Linux/ppd'
 ( cd '/usr/share/cups/model' && rm -f lm400.ppd lm450.ppd lmpc.ppd lmpc2.ppd lmpnp.ppd lp350.ppd lw300.ppd lw310.ppd lw315.ppd lw320.ppd lw330.ppd lw330t.ppd lw400.ppd lw400t.ppd lwduol.ppd lwduot.ppd lwduot2.ppd lwtt.ppd lw4xl.ppd lw450.ppd lw450t.ppd lw450tt.ppd lw450dl.ppd lw450dt.ppd se450.ppd )
make[1]: Leaving directory '/home/me/DYMO-SDK-for-Linux/ppd'
Making uninstall in docs
make[1]: Entering directory '/home/me/DYMO-SDK-for-Linux/docs'
make[1]: Nothing to be done for 'uninstall'.
make[1]: Leaving directory '/home/me/DYMO-SDK-for-Linux/docs'
Making uninstall in samples
make[1]: Entering directory '/home/me/DYMO-SDK-for-Linux/samples'
Making uninstall in paper_bounds
make[2]: Entering directory '/home/me/DYMO-SDK-for-Linux/samples/paper_bounds'
make[2]: Nothing to be done for 'uninstall'.
make[2]: Leaving directory '/home/me/DYMO-SDK-for-Linux/samples/paper_bounds'
Making uninstall in paper_list
make[2]: Entering directory '/home/me/DYMO-SDK-for-Linux/samples/paper_list'
make[2]: Nothing to be done for 'uninstall'.
make[2]: Leaving directory '/home/me/DYMO-SDK-for-Linux/samples/paper_list'
Making uninstall in test_label
make[2]: Entering directory '/home/me/DYMO-SDK-for-Linux/samples/test_label'
make[2]: Nothing to be done for 'uninstall'.
make[2]: Leaving directory '/home/me/DYMO-SDK-for-Linux/samples/test_label'
Making uninstall in custom_paper
make[2]: Entering directory '/home/me/DYMO-SDK-for-Linux/samples/custom_paper'
make[2]: Nothing to be done for 'uninstall'.
make[2]: Leaving directory '/home/me/DYMO-SDK-for-Linux/samples/custom_paper'
Making uninstall in custom_paper_tape
make[2]: Entering directory '/home/me/DYMO-SDK-for-Linux/samples/custom_paper_tape'
make[2]: Nothing to be done for 'uninstall'.
make[2]: Leaving directory '/home/me/DYMO-SDK-for-Linux/samples/custom_paper_tape'
make[2]: Entering directory '/home/me/DYMO-SDK-for-Linux/samples'
make[2]: Nothing to be done for 'uninstall-am'.
make[2]: Leaving directory '/home/me/DYMO-SDK-for-Linux/samples'
make[1]: Leaving directory '/home/me/DYMO-SDK-for-Linux/samples'
make[1]: Entering directory '/home/me/DYMO-SDK-for-Linux'
make[1]: Nothing to be done for 'uninstall-am'.
make[1]: Leaving directory '/home/me/DYMO-SDK-for-Linux'

```
I'll stop here for now until I hear back from you, I would like to see all your output from the terminal please.

---

### Post by jgw on 2023-06-12
sudo make uninstall failed again (see below - went to man make and there is no 'uninstall' anyplace)  

my version of make:
greg@greg-HP-EliteBook-8560p:~/DYMO-SDK-for-Linux$ make -version
GNU Make 4.3
Built for x86_64-pc-linux-gnu
Copyright (C) 1988-2020 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Here is the stuff you requested:
greg@greg-HP-EliteBook-8560p:~$ cd ~/ && ls
'Abbey Lincoln - Queens Of Vocal Jazz - Affair.mp3'   Pictures
'Calibre Library'                                     Public
 Desktop                                              snap
 Documents                                            system-info-link.log
 Downloads                                            system-info.txt
 DYMO-SDK-for-Linux                                   temp
 kodi_crashlog-20230416_152546.log                    Templates
 Music                                                Videos
'pass stuff'
greg@greg-HP-EliteBook-8560p:~$ cd DYMO-SDK-for-Linux && ls
aclocal.m4      configure.ac  dymo-cups-drivers.spec  Makefile.am    ppd
AUTHORS         COPYING       INSTALL                 missing        README.md
autom4te.cache  depcomp       install-sh              mkinstalldirs  samples
ChangeLog       docs          LICENSE                 NEWS           src
greg@greg-HP-EliteBook-8560p:~/DYMO-SDK-for-Linux$ sudo make uninstall
[sudo] password for greg: 
Sorry, try again.
[sudo] password for greg: 
make: *** No rule to make target 'uninstall'.  Stop.
greg@greg-HP-EliteBook-8560p:~/DYMO-SDK-for-Linux$

---

### Post by jgw on 2023-06-15
I think you want this:
greg@greg-HP-EliteBook-8560p:~$ cd -~ && ls
bash: cd: -~: invalid option
cd: usage: cd [-L|[-P [-e]] [-@]] [dir]
greg@greg-HP-EliteBook-8560p:~$ cd ~/ && ls
'Abbey Lincoln - Queens Of Vocal Jazz - Affair.mp3'   Pictures
'Calibre Library'                                     Public
 Desktop                                              snap
 Documents                                            system-info-link.log
 Downloads                                            system-info.txt
 DYMO-SDK-for-Linux                                   temp
 kodi_crashlog-20230416_152546.log                    Templates
 Music                                                Videos
'pass stuff'
greg@greg-HP-EliteBook-8560p:~$ cd DYMO-SDK-for-Linux && ls
aclocal.m4      configure.ac  dymo-cups-drivers.spec  Makefile.am    ppd
AUTHORS         COPYING       INSTALL                 missing        README.md
autom4te.cache  depcomp       install-sh              mkinstalldirs  samples
ChangeLog       docs          LICENSE                 NEWS           src
greg@greg-HP-EliteBook-8560p:~/DYMO-SDK-for-Linux$ sudo make uninstall
[sudo] password for greg: 
make: *** No rule to make target 'uninstall'.  Stop.

---

### Post by #&amp;thj^% on 2023-06-16
That looks to me like it never installed, at least not a proper install.
jgw I hate to be the barer of bad news but I would ask for a refund if possible.
There are others out there that just work with Linux and or Bluetooth.
Even phone apps.
EDIT: Or even install Windows in a VM for the Drivers and a working label printer.

---

### Post by jgw on 2023-06-16
This morning I just thought I would look at printer in settings.  I will try and send a picture.  Basically, my dymo is now working!  I have no idea how or why.  I do remember is was in [http://localhost:631/admin](http://localhost:631/admin) and setup the dymo from there and it seemed to work but I never tested it until this morning.  Have no idea how I got there or what it really is but that worked for me.  Now all I have to do is to get the canon mp980 working.  It has always worked with the gutenprint (I have gutenprint-5.3.3 in my downloads folder but have no idea what to do with it).  

I have no idea what is going on.

---

### Post by #&amp;thj^% on 2023-06-16
Hey Hey that's a good thing.
and this " http://localhost:631/admin" is the front end for CUPS or GUI if you will.
And  the canon mp980 is something I'm not familiar with but plenty here in the forums can help you there.
BTW it would be a good idea to start browsing for replacement label printers, since Dymo no longer has any interest in Linux now.

---

### Post by jgw on 2023-06-16
I have tried the dymo.  It has a problem in that its only writing 3/4" when it should be something like 1.6" on one label and 3" long on the other one but it only goes 3/4".  It knows how long the labels are (I an press one out and it stops correctly).  I have no idea what this means.  I have dropped them a note and see if they can tell me where I screwed up.  

thank you for your help.  Without it I would have given up.  Thanks again!

---

### Post by #&amp;thj^% on 2023-06-16
> **jgw said:**
> I have tried the dymo.  It has a problem in that its only writing 3/4" when it should be something like 1.6" on one label and 3" long on the other one but it only goes 3/4".  It knows how long the labels are (I an press one out and it stops correctly).  I have no idea what this means.  I have dropped them a note and see if they can tell me where I screwed up.  

thank you for your help.  Without it I would have given up.  Thanks again!

This is not how I like to leave a support thread, but I can offer some suggestions here for trial:
print very long text on a tape:
```
lpr -o landscape -o PageSize=24_mm__1___Label__Auto_ docs/test.txt

```

set printing options specific to the LabelWriter driver:
```
lpr -o PageSize=30252_Address -o PrintQuality=Graphics -o PrintDensity=Light docs/test.txt

```

set printing options specific to the LabelManager driver
```
lpr -o PageSize=Address_Label -o CutOptions=ChainMarks -o LabelAlignment=Right -o TapeColor=1

```

---

### Post by jgw on 2023-06-17
Thanks for the reply and the help.  I will do your suggestions.  I screwed around a bit with glabels and am getting a bit more.  I will let you know the results.

---

### Post by jgw on 2023-06-17
I went back to settings, clicked on printer details then "select from database" then "dymo labelwriter-400-turbo"  then I got "dymo:0/cups/model/lw400t.ppd".  I suspect this might be in "DYMO SDK for linux" but not sure.  Just found it.  Now, what do I do with it?

Thoughts?

Tried your suggestion but need test.txt for any to do anything:
greg@greg-HP-EliteBook-8560p:~$ lpr -o landscape -o PageSize=24_mm__1___Label__Auto_ docs/test.txt
lpr: Error - unable to access "docs/test.txt" - No such file or directory

Where do I find test.txt?

---

### Post by #&amp;thj^% on 2023-06-17
Greg I'm not sure your even using the patch, but if you are then look in "cd DYMO-SDK-for-Linux" and this " README.md"

---

### Post by jgw on 2023-06-17
I have no idea what "the patch" means but I do have DYMO-SDK-for-Linux.  That being the case.  The first part is installation and wants me to do stuff.  So:[https://paste.ubuntu.com/p/XM4X4dJpJR/](https://paste.ubuntu.com/p/XM4X4dJpJR/)

doing the dymo-sdk-for-linux (it seemed to do a lot of stuff!)

---

### Post by #&amp;thj^% on 2023-06-17
The Patch includes code needed to run your Dymo on the New cups version.
But I have bad news after speaking with him: [https://github.com/Kyle-Falconer/DYMO-SDK-for-Linux/pull/12](https://github.com/Kyle-Falconer/DYMO-SDK-for-Linux/pull/12) 
There is a suggested change there if you can follow it. It fails on yours and mine with:
```
make[1]: *** [Makefile:300: all] Error 2
make[1]: Leaving directory '/home/me/DYMO-SDK-for-Linux/src'
make: *** [Makefile:365: all-recursive] Error 1

```

I'm going offline for the Day now, work work.
I'll check back later tonite or tomorrow for sure

**EDIT: Here is the correction to that error**
So i just corrected the syntax in "/home/me/DYMO-SDK-for-Linux/src/common/"
And add this line to "CupsPrintEnvironment.cpp"
Like this:
```
// Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA  02111-1307, USA.

#include <stdio.h>
#include <string>
#include "CupsPrintEnvironment.h"
#include <errno.h>
#include <cups/cups.h>
#include <cups/sidechannel.h>
#include <cassert>

namespace DymoPrinterDriver
{

```
The line was "#include <cups/sidechannel.h>"
Now finish with your install

---

### Post by jgw on 2023-06-17
I did as you said.  I think, then, I am supposed to do the readme.md and do the installation again.  I am completely confused.  But its ready for you to tell me to have at it!

After I did the first readme.md (sent you all of it) I then went to settings/printers/labelwriter/select from database and choose the dymo-labelwriter-400-turbo.  It then told me to install driver dymo:"0/cups/model/lw400t.ppd", which I did. Then I tried printing stuff.  We are getting close!  I can, right now run dymo 30336 (1" x 2.125)  but fail with 30252 (1.125 x 3.500)  I am not sure about the driver thing. I took a look at it and I think I can actually tell it what labels to use by just getting rid of x's before stuff.  I'll dink a bit on that.

Now, for the 'patch'  I am absolutely ignorant on that and have no idea if I am using it or not.

I understand the work thing.  I am retired (for quite a while - but took most of this week getting operated on and getting a pacemaker)  Not much fun 

I attached another picture so you can tell where I am.  If I run the readme.md that will reconstitute the driver I am using so I guess I will have to install it again (not really sure but makes sense)

Later!

---

### Post by #&amp;thj^% on 2023-06-18
Your not quite yet ready, now you need to "cd DYMO-SDK-for-Linux"
And finish with 
```
make
sudo make install

```
If there are errors please stop and paste them here before going on. :)

---

### Post by jgw on 2023-06-19
Here is Make  and  sudo make install:
[https://paste.ubuntu.com/p/d2Z74d3yGN/](https://paste.ubuntu.com/p/d2Z74d3yGN/)

Now, for the 'patch' I remain ignorant on that and have no idea if I am using it or not.

I ran the Labelwriter.  It worked with the 1 x 2.125 label but failed with the 1.125 x 3.500

---

### Post by #&amp;thj^% on 2023-06-19
I did not see "make" used from you link just "make install", but non the less it looked like it succeeded.
Some report a restart is needed after the SDK install. (we will call it that instead of patch)
It will be a trial error making it work the way you want it to.
The ReadMe will help you and there are some samples there to get you started.

---

### Post by jgw on 2023-06-20
I have now installed three different labels.  2 are working just fine and one is not.  What I have been trying to do, and failing, is just removing the one that has the problem and re-enter.  I know its possible I just forget how.   Oh, and one I tried to make more copies but I had to do them one at a time as it didn't want to run any copies.  I will continue to have at it.  Did you know that there is also a manual on glabels?  Its not all that detailed but its there!

---

### Post by #&amp;thj^% on 2023-06-20
Have you forgot this page: [http://localhost:631/printers/](http://localhost:631/printers/).
I know nothing about glables sorry.

---

### Post by jgw on 2023-06-21
Yep!  I wish I did know something about glabels too!  I continue to do battle, however................

---

