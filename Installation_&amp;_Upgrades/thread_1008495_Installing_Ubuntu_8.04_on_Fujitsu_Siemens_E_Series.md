---
title: "Installing Ubuntu 8.04 on Fujitsu Siemens E Series Lifebook E8020"
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by Hopefully_informative on 2008-12-11
I have successfully installed Ubuntu 8.04 on my Fujitsu Siemens E Series LifeBook, model E8020D
 :-)

Here is how I did it:


1. Preparations

   a) Plug the AC outlet adapter into your Lifebook.

   b) Connect the LAN cable to the back of you laptop



2. Setting BIOS correctly.

   a) Turn on the laptop and hit F2 to enter BIOS

   b) Move to the Info tab and see if you have the same BIOS as me



        BIOS Version: 1.10

        BIOS Date    08/17/2005



	CPU Type:     Intel(R) Pentium(R) M Processor 760

	CPU Speed:    2.00 GHz

	

	Total Memory: 1024 MB



      (If you have a different BIOS version, that should be OK too)

   c) Move to the Exit tab, select "Load Setup Defaults" and confirm this
      option

   d) Move to the Advanced tab and open the Internal Device Configuration
      dialogue.

      ********************************************************************

      ** Disable the AHCI. THE INSTALL FAILS IF YOU FORGET TO DO THIS ! **

      ********************************************************************

   e) Move to the Boot tab and open the Boot Device Priority dialoge.
      Move "CD-ROM" to the top.

   f) Open the CD tray and place the Ubuntu 8.04 Install CD in it. 

   g) Close the CD tray

   h) Exit BIOS, using the "Exit Saving Changes" choice. Confirm. 
      The laptop will no boot from the install CD.



2. Installing Ubuntu

   a) There is nothing special during this step. 

      Once the PC starts the "Select and install software" step, it runs
      unattended for approximately 32 minutes.

      (I used the "alternate" installation CD, but that should not matter)

   b) At the end of the intstallation the CD pops out automatically.
      Remove it and allow Ubuntu to boot.



3. Booting into Ubuntu for the first time.

   a) Let the fresh install sit idle for a few seconds, with internet
      access. After a few seconds
 a small pop-up messages informs you
      updates are available. Install them.

  

4. Setting up the wireless network 
   a) If you are running an encrypted wireless network, the wireless
      network card
 can't connect to your wireless network until you
      supply Ubuntu with the encryption key.
      So, select:

           System | Administration | Network tools | Unlock

           After authenticating, click Wireless Network, and Properties

           Uncheck Enable roaming mode, and:

                Select your SSID from the pulldown list (or type it in, 
                if hidden)

                Select the correct Password type

                Enter the wireless network password, and click OK.

           After 5-10 seconds you should be connected. 


      My personal tip: If you are having wireless connection problems, 
                       FIRST MAKE 100% SURE YOU ENTERED THE CORRECT
                       ENCRYPTION KEY,
                       before you go looking for other problem causes! 



5. Enabling Noscript and Flash in Firefox

   a) Point Firefox to [www.adobe.com](www.adobe.com) and download Adobe Flash Player, 

      select ".deb fo Ubuntu 8.04+" in the pull-down list.

      Accept Gdbi to be used as Package Installer and click to install.

      Restart Firefox. You shouild now be able to view Flash content,

      but not hear any audio (We'll fix the audio later, see below)

       

       (Note: I first tried installing the 'flashplugin-nonfree' package
              in Synaptic,
 but for some reason this plugin was not able
              to play Flash content.
 
              I.e. in my experience you HAVE TO go [www.adobe.com](www.adobe.com) to get
              the correct player.)


   b) To install NoScript, point Firefox to addons.mozilla.org
,
      search for 'noscript' and click 'Add to Firefox' in the search 
      result.

      Remember: From now on, you have to pay attention to NoScript's 
                icon in the lower left-hand corner when browsing.



6. Enable audio

   a) Click on an mp3 file, and Totem Movie Player starts. It immedeately
      suggests installing
 GStreamer ffmpeg video plugin and 
      GStreamer extra plugins. Check both and click to install.
      (Yes, there are ways to install these two codec packs from the
       command line, but this ways is easier, I think)
      If you plug in a headset you should now have music playing.

   b) To enable sound output from the internal speaker, click on the
      speaker icon
 (located close to the red Off button in the upper 
      right hand corner of the screen).

      In the Volume COntrol: HDA Intel (ALsa mixer) window, click the 
      red X under "Internal speaker"

      and push the stereo volume slider up. You should now hear music.


When you get to this point you have a laptop that works nicely indeed :-)
Did I mention that the glidepoint works out-of-the-box, with vertical scrolling enabled?

---

