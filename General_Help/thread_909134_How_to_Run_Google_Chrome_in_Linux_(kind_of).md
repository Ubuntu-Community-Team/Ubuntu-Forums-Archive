---
title: "How to: Run Google Chrome in Linux (kind of)"
date: 2008-09-03
forum: General Help
---

### Post by janmartin on 2008-09-03
Hi all,

as of today (3. Sep. 2008) the new Goggle Chrome browser is available. 
Unfortunately there is no Linux Chrome version yet, but you can run it without:

[http://data.mybestprojects.com/Google_Chrome_Ubuntu_8.04_VirtualBox_seamless.png](http://data.mybestprojects.com/Google_Chrome_Ubuntu_8.04_VirtualBox_seamless.png)

So this is what to do:
1) Install[ VirtualBox]("http://www.virtualbox.org") virtual machine from Sun: [http://www.virtualbox.org](http://www.virtualbox.org)

2) Create a new virtual machine with an Windows XP licence you have lying around.

3) Install Guest Additions into Windows to enable Cut and Paste between Ubuntu and Windows.

4) Install Chrome from
[http://build.chromium.org/buildbot/snapshots/chromium-rel-xp/1648/](http://build.chromium.org/buildbot/snapshots/chromium-rel-xp/1648/)

5) Activate seamless mode 
Menu -> Machine -> Seamless Mode or CTRL+L)

DONE!

P.S.:
Chrome runs snappy and can be used for every-day-surfing.
I tested youtube, flickr and a dozen other sites. They  all  work nice. 
Only thing it needs is lots of RAM. I recently upgraded my Acer Aspire 5630 notebook from 1 GB RAM to 4 GB RAM. With just 1 GB of RAM VirtualBox but was to slow for everything except testing. Now I dedicate 1 GB to the virtual machine alone. What a difference!

P.S.2:
Google about  readiness of Linux Chrome:

[http://dev.chromium.org/developers/how-tos/build-instructions-linux](http://dev.chromium.org/developers/how-tos/build-instructions-linux)

[COLOR="Red"]**...There is no working Chromium-based browser on Linux.**[/COLOR] 
Although many Chromium submodules build under Linux and a few unit tests pass, all that runs is a command-line "all tests pass" executable....

Also Chrome does not work with WINE. Not even with newest  unstable 1.1.3 version.

P.S.3:
Technical stuff:

When creating the VirtualBox Windows XP virtual machine 
- set "Base memory size" to 1 GB of RAM.
- create a "Dynamically expanding Image" of 4 GB as HDD.
- set audio to "Pulse". 
- in Settings set the "Video Memory Size" slider to the middle.

Windows XP:
I deactivated unnecessary graphic effects:
- Rightclick on desktop, click Properties, tab Appearance, button Effects. Untick everything.
And last but not least:
Install free (for personal use) Virus scanner: [http://www.free-av.com](http://www.free-av.com)

Good luck!
Jan

---

### Post by meborc on 2008-09-03
so basically you need to install windows to try out chrome... :D

i would wait for the linux version... to run virtual machine just to browse web - scary

:shock:

---

### Post by Bradtek on 2008-09-03
What does it do that Firefox / Opera / Insertbrowsername here, doesnt ?

---

### Post by philinux on 2008-09-03
Might try it with Wine for a laugh.

[edit] No diced as expected.

---

### Post by overdrank on 2008-09-03
Moved to General Help as I believe it does not need to be in ABT
:)

---

### Post by Dougie187 on 2008-09-03
Here is a 37 page comic describing it.
[http://www.google.com/googlebooks/chrome/](http://www.google.com/googlebooks/chrome/)

You can get most of the information in the first couple slides.

---

### Post by ronnielsen1 on 2008-09-03
> Might try it with Wine for a laugh.
If they allowed you to download it. They pick me up as linux and tell me it's a nogo.
I hate when places automatically assume what you want to dl because I've downloaded the windows version of firefox so my kid can play shockwave but it tried to stop me.

---

### Post by gardara on 2008-09-03
> **ronnielsen1 said:**
> If they allowed you to download it. They pick me up as linux and tell me it's a nogo.
I hate when places automatically assume what you want to dl because I've downloaded the windows version of firefox so my kid can play shockwave but it tried to stop me.

You could fake your user agent and download it that way... 

[http://dl.google.com/tag/s/appguid%3D%7B8A69D345-D564-463C-AFF1-A69D9E530F96%7D%26iid%3D%7B8A984A81-E33F-536A-94FA-6528E0F5EFA3%7D%26lang%3Den%26browser%3D2%26usagestats%3D1%26appname%3DGoogle%2520Chrome%26needsadmin%3Dfalse%26appguid%3D%7B00058422-BABE-4310-9B8B-B8DEB5D0B68A%7D%26appname%3DChromeGears%26needsadmin%3Dfalse/update2/installers/ChromeSetup.exe](http://dl.google.com/tag/s/appguid%3D%7B8A69D345-D564-463C-AFF1-A69D9E530F96%7D%26iid%3D%7B8A984A81-E33F-536A-94FA-6528E0F5EFA3%7D%26lang%3Den%26browser%3D2%26usagestats%3D1%26appname%3DGoogle%2520Chrome%26needsadmin%3Dfalse%26appguid%3D%7B00058422-BABE-4310-9B8B-B8DEB5D0B68A%7D%26appname%3DChromeGears%26needsadmin%3Dfalse/update2/installers/ChromeSetup.exe)

Is a direct link from where I got it... might work, otherwise, just install user agent switcher extension for firefox....

---

### Post by Unlimited1 on 2008-09-03
or you could just run it under Linux...

[http://dev.chromium.org/developers/how-tos/build-instructions-linux]("http://dev.chromium.org/developers/how-tos/build-instructions-linux")

---

### Post by Joeb454 on 2008-09-03
> **Unlimited1 said:**
> or you could just run it under Linux...

[http://dev.chromium.org/developers/how-tos/build-instructions-linux]("http://dev.chromium.org/developers/how-tos/build-instructions-linux")

Last I heard, it wouldn't build and run correctly. As mentioned earlier in this thread

---

### Post by kpkeerthi on 2008-09-03
> **Unlimited1 said:**
> or you could just run it under Linux...

[http://dev.chromium.org/developers/how-tos/build-instructions-linux]("http://dev.chromium.org/developers/how-tos/build-instructions-linux")

> Note: There is no working Chromium-based browser on Linux. Although many Chromium submodules build under Linux and a few unit tests pass, **[COLOR="Red"]all that runs is a command-line "all tests pass" executable[/COLOR]**.
... from [http://dev.chromium.org/developers/how-tos/build-instructions-linux](http://dev.chromium.org/developers/how-tos/build-instructions-linux)

---

### Post by KingWilliam on 2008-09-03
Why would you want to run a browser in a VM. It will slow down your computer like hell.

I'll just wait untill the linux version gets released.

---

### Post by kdwillia on 2008-09-03
> **KingWilliam said:**
> Why would you want to run a browser in a VM. It will slow down your computer like hell.

I'll just wait untill the linux version gets released.

What is extremely funny is that many of us used to run windows with Linux in a VM to surf the web without worries of virus and spyware.   Now we are running Linux and using a VM of Windows just to use a new browser???   FAIL

---

### Post by billgoldberg on 2008-09-03
> **KingWilliam said:**
> Why would you want to run a browser in a VM. It will slow down your computer like hell.

I'll just wait untill the linux version gets released.

Same here.

---

### Post by god0fgod on 2008-09-03
Does it work in Wine? I'm just going to wait like everyone else. It's probably not that spectacular anyway.

---

### Post by hardwyrd on 2008-09-04
Ran it on Wine 1.1.3 but no HTTPS as of yet. Bug report to WineHQ was made. Its not really a Wine bug per se, however, there might be other workarounds until the Linux version is ready.

[http://baudizm.blogsome.com/2008/09/03/google-chrome-on-wine/](http://baudizm.blogsome.com/2008/09/03/google-chrome-on-wine/)

---

### Post by janmartin on 2008-09-04
This is a nice description how to run Chrome in Wine 1.3.3:

[http://ubuntuforums.org/showpost.php?p=5719331&postcount=45](http://ubuntuforums.org/showpost.php?p=5719331&postcount=45)

When you got this working, goto youtube.com, click a video and download the flash installer install_flash_player.exe
Doublclick to install. Restart Chrome. Youtube videos and other flash stuff now works.

Jan

---

### Post by coolen on 2008-09-08
My hope is that Firefox and others will be able to incorporate some of the new features in Chrome. Some of these would be easier than others, but the V8 Javascript engine is supposedly very portable.

---

