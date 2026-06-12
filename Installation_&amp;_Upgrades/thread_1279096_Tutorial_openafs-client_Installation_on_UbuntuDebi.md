---
title: "Tutorial: openafs-client Installation on Ubuntu/Debian"
date: 2009-09-30
forum: Installation &amp; Upgrades
---

### Post by Lumberg on 2009-09-30
Hey all,

Just thought I'd share this with you.  It took me a while to find and figure out how to do this, so here's the information on how to install open-afs-client on your Debian/Ubuntu system.  Shout out to Bryon W. at IBM who figured this out.

Debian does not come with the openafs-modules pre-built, as you might have already found out-- so you will have to get the source and do the compilation yourself, which is actually pretty easy using a sweet little package called module-assistant.

**Get and install the required packages:**

[FONT=Courier New][COLOR=Blue]sudo apt-get install openafs-client openafs-modules-source[/COLOR][/FONT]

Configure your CellServDB.  It's generally easiest to get your hands on the CellServDB and ThisCell files from another machine and just put them in your /etc/openafs/ directory.

**Configure openafs modules:**

[FONT=Courier New][COLOR=Blue]sudo apt-get install module-assistant
sudo module-assistant prepare openafs-modules
sudo module-assistant auto-build openafs-modules[/COLOR][/FONT]

**Install the module:**

[FONT=Courier New][COLOR=Blue]sudo m-a install openafs-modules-source[/COLOR][/FONT]

**Start up the daemon:**

You'll have to use force-start.  If you just use "start" nothing will happen, most likely.  Look for "afsd: All AFS daemons started." to be printed.

[FONT=Courier New][COLOR=Blue]sudo /etc/init.d/openafs-client force-start[/COLOR][/FONT]

Then-- enjoy.  Make sure to klog and sign in!

If you don't want afs to start on boot, in case you have to VPN into a network first, you'll have to disable it from starting automatically.

[FONT=Courier New][COLOR=Blue]sudo update-rc.d -f openafs-client remov[/COLOR][/FONT][COLOR=Blue]e[/COLOR]

Then you'll have to do your force start command from above whenever you want to use it.

Hope this helps--
Nick

---

### Post by Lars Noodén on 2009-10-01
> **Lumberg said:**
> 
If you don't want afs to start on boot, in case you have to VPN into a network first, you'll have to disable it from starting automatically.

[FONT=Courier New][COLOR=Blue]sudo update-rc.d -f openafs-client remov[/COLOR][/FONT][COLOR=Blue]e[/COLOR]

Then you'll have to do your force start command from above whenever you want to use it.


Thanks!  That is concise!

Couldn't [FONT=Courier New]**update-rc.d**[/FONT] be set so that automatic startup of AFS follows startup of boondoggles like VPNs?

---

### Post by Lumberg on 2009-10-02
> **Lars Noodén said:**
> Thanks!  That is concise!

Couldn't [FONT=Courier New]**update-rc.d**[/FONT] be set so that automatic startup of AFS follows startup of boondoggles like VPNs?

Actually, yeah-- I've never tried that but it's an intriguing idea.  :-)

---

