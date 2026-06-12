---
title: "The Canon PIXMA iP1800, redux"
date: 2010-12-07
forum: Hardware
---

### Post by owlcroft on 2010-12-07
I have plodded through an estimated 6,641 of the estimated 478,594 threads on how to make this creature work in Ubuntu, and no two seem quite to agree.

Here is what I have and what I have done, and I hope someone can help me out.

I am working with a fresh install of Maverick, fully updated from all major repositories.  It is the 64-bit version, and I already had **ia32-libs** installed (from grinding through the Google Earth install).

I have installed the version 2.70 Canon Linux drivers (2.70.01.010, to be exact) via Alan Sanford's script, the crux of which is:

```
    cd ./files
    dpkg -i --force-architecture cnijfilter-common_2.70-2_i386.deb
    dpkg -i --force-architecture cnijfilter-ip1800series_2.70-2_i386.deb
    ln -s libpng12.so.0.27.0 /usr/lib32/libpng.so.3
    ln -s libtiff.so.4.2.1 /usr/lib32/libtiff.so.3
    cp -p /usr/share/cups/model/canonip1800.ppd /usr/share/cups/model/canonip1800.ppd_backup
    cp canonip1800.ppd /usr/share/cups/model
    /etc/init.d/cups force-reload
```

Just for completeness' sake, let me show what the ppd file changes introduced were.  This--
```
*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600
*Resolution 600/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*CloseUI: *Resolution
```--was changed to this:
```
*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600
*Resolution 300/300 dpi: "<</HWResolution[300 300]>>setpagedevice"
*Resolution 600/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*Resolution 1200/1200 dpi: "<</HWResolution[1200 1200]>>setpagedevice"
*Resolution 2400/1200 dpi: "<</HWResolution[2400 1200]>>setpagedevice"
*Resolution 4800/1200 dpi: "<</HWResolution[4800 1200]>>setpagedevice"
*CloseUI: *Resolution

*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 3
*CNQuality 2/High: "2"
*CNQuality 3/Normal: "3"
*CNQuality 4/Standard: "4"
*CNQuality 5/Economy: "5"
*CloseUI: *CNQuality

*OpenUI *CNGrayscale/Grayscale: Boolean
*DefaultCNGrayscale: False
*CNGrayscale True/Yes: True
*CNGrayscale False/No: False
*CloseUI: *CNGrayscale
```



Now I plug the Canon USB cable in, and the system at once notices that the printer, properly identified, is connected.  When I go to System-Administration-Printing and Click **Add+**, *Canon iP1800* shows up nicely in the drop-down list.  If I select it, then click **Forward**, I get a *searching for drivers* message, followed by the **Describe Printer** page; after filling that out (the entries are not critical), and clicking **Apply**, the printer is installed, and I get a *Would you like to print a test page?* popup query (which I choose at first to **Cancel**).

The printer and drivers now appear to be 100% successfully installed.  A check of the properties page for the printer shows everything that should be there.  But . . . ah, yes, *But*.  If I click on **Print Test Page**, nothing happens; yet if I bring up the **Manage Print Jobs** window, and click on **Show completed jobs**, there it is, fat and sassy, labelled as *Completed*, just as if it had worked to perfection.  Everything is wonderful, except that the printer has done absolutely nothing.  (Yes, it is on; yes, it is loaded with paper of the right size, orientation, and quantity; no, the orange warning light is not flashing.)

The only other "trick" I tried--to no avail--was making a symbolic link to duplicate the *cups* pointer as *cupsys* (and I after removed it).

From what I have read, others have successfully used those 2.70 drivers under Maverick, though I know there are at least 3.00-level ones running about somewhere.

Can anyone please help me out here?  Thanks.

---

### Post by owlcroft on 2010-12-09
(bump)

Surely after all the fuss over the years about this printer, someone must have some ideas . . . .

---

### Post by owlcroft on 2010-12-11
Fixed!

What a nightmare.  But finally, pulling together bits and pieces of information from here and there, and doing a lot of looking up of things, it all comes down to issuing two simple commands:

  sudo ln -s /usr/lib32/libtiff.so.4 /usr/lib32/libtiff.so.3
  sudo ln -s /usr/lib32/libpng.so /usr/lib32/libpng.so.3

The Canon drivers are looking for a couple of old library files, so we just have to point them at the correct new ones.  And because we have pointed them at generic links, they should continue to work through Ubuntu updates (or at least till libtiff.so.4 is superseded).

To reiterate the whole process:

**INSTALLING A CANON iP1800 ON UBUNTU:**

1. Get the Debian (.deb) packages for the needed pair of "filters" as made by Canon and distributed in areas other than North America.  The ones I got were named:

. cnijfilter-common_2.70-2_i386.deb
. cnijfilter-ip1800series_2.70-2_i386.deb

You need them both.  There are similar .deb packages running around other slightly different names, and also a 3.00 version (as opposed to the 2.70 versions listed above).  Almost surely, any of them will work.  The source I used was:

. *[http://www.blogternals.com/2009/07/09/canon-ip1800-ubuntu/](http://www.blogternals.com/2009/07/09/canon-ip1800-ubuntu/)*

Just do ***not*** run the install script that comes with whatever package you get, as it is almost surely out of date and won't do the job correctly.

You will probably get your package, no matter whence, in the form of a single tar.gz file.  Download it to any convenient spare directory (such as Downloads), right-click on it, and choose--

**Extract here**

--from the drop-down menu.  It will make its own subdirectory, so don't worry about any mess.  You should end up with at least three files, maybe more: two .deb packages, a .ppd file, and possibly an installer script and maybe even a README file.  The deb and ppd packages will probably be in a subfolder named **files**.  That is where you want to work from.


2. Make sure the supplied PPD file is from Canon and matches the version of the drivers you have (2.70 or 3.00 or whatever).  The one I got was named:

. **canonip1800.ppd**

Look into the file (it is plain text) and check the version number down at the very bottom against the filters.


3. If you are installing on a 64-bit system, make sure that you have first already installed (via Synaptic) the [package:

. ia32-libs

If not, install it now.


4. Install the Canon drivers with the following commands:

sudo dpkg -i --force-architecture cnijfilter-common_2.70-2_i386.deb
sudo dpkg -i --force-architecture cnijfilter-ip1800series_2.70-2_i386.deb

BE SURE you do them in the order shown.


5. Move or copy the canonip1800.ppd file to:

. /usr/share/cups/model

(If there is already a like-named PPD file there, make a backup copy of it under some likely name, such as canonip1800.ppd.old)


6. Run the two link-making commands given earlier:

  sudo ln -s /usr/lib32/libtiff.so.4 /usr/lib32/libtiff.so.3
  sudo ln -s /usr/lib32/libpng.so /usr/lib32/libpng.so.3


7. Actually install the printer.  Make sure that it is connected by its USB cable, is powered on, and is loaded with a modest (not large) amount of paper in the correct alignment ("portrait")--see the printer manual.  In Ubuntu, click on--

. **System - Administration - Printing**


8. Click on the prominent green "**Add+**" button.  A drop-down list will appear with the iP1800 in it.  Select it, then click the **Forward** button.


9. A "searching for drivers" wait box will appear; soon after, the system will discover the drivers and give you a screen with three data lines for entry (with suggested text).  What you enter here is not important.  I like to use (in order):

iP1800
Canon iP1800 color printer
xxxx's desktop

(where you are xxxx, or substitute anything else useful to you).

Click the "**Apply**" button when you're done.

That's it.  You can now right click on the iP1800 in the Ubuntu "Printing" box and get a properties popup box.  Most or all of the several screen's worth of settings should be fine at their default settings.  After reviewing them, click on the button to print a Test Page, and admire your handiwork.

_Later Add:_
a. Be sure you do in fact have both the libtiff and libpng packages installed (I no longer recall if they come by default or need to be added).  Check via Synaptic.  They would be **liftiff4** and **libpng12-0** (I don't know if **libpng3** is needed).

b. This same "fix" of links might also work for some number of other Canon drivers that seem installed but don't seem to actually work.

c. The defective install scripts, which set up links to older (and, in some cases, particular version-number) libraries would explain why drivers that used to work stopped doing so at some point.

---

