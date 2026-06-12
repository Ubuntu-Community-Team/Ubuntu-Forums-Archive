---
title: "download limit checker"
date: 2008-10-03
forum: General Help
---

### Post by Bari on 2008-10-03
Hi, I have recently changed from a 1mg unlimited download to a 8mg limited download ISP is there an applet or small programme I can install that will let me keep a check on what I'm downloading. I also need java, so I can use the BT speedtester site.  What should I install for that pse.

---

### Post by Zill on 2008-10-03
I never found such a program or applet but my ISP account (madasafish.com) has webpages that show my historical broadband usage on a daily basis.

Regarding java, open Synaptic package manager then

Remove:
openjdk
icedtea
gcjwebplugin

Install:
sun-java-bin
sun-java-jre
sun-java-plugin

Job done :-)

---

### Post by Bari on 2008-10-04
Thanks for that, I also have download information on my BThomehub but I think they are ripping me off as the two updates of 8.4mg and 8.0mg have registered as 9.75mg and 9.6mg respectivly. In fact if I open the page on the hub it registers as a 0.3mg download which to my mind it shouldn't as I'm not downloading anything from the net just looking at the internal workings of the hub.  As to the java I have those packages already installed.   I am told that  speedtest.bt.com  will only work with internet explorer. Anyway thanks for the reply.

---

### Post by Zill on 2008-10-04
> **Bari said:**
> ...I am told that  speedtest.bt.com  will only work with internet explorer...
Don't know who told you that but this is directly from the [http://speedtester.bt.com/]("http://speedtester.bt.com/") home page...
> The performance tester has been successfully tested with the following browsers; Firefox, Opera, Netscape, Microsoft Internet Explorer and Safari.
I have just run the test using Firefox 1.5 with no problems at all (apart from the slow BT server!).

---

### Post by Zill on 2008-10-04
You may find these links useful if you want to test java and other goodies...

[http://javatester.org/version.html]("http://javatester.org/version.html")

[http://www.w3.org/People/mimasa/test/object/java/clock]("http://www.w3.org/People/mimasa/test/object/java/clock")

[http://kb.mozillazine.org/Testing_plugins]("http://kb.mozillazine.org/Testing_plugins")

---

### Post by geezerone on 2009-02-10
Know this is an old thread but just get grey rectangular box a top of screen when going to btspeedtest page. At first it said in a yellow box, that missing plugins were missing.

I installed gcj and gcj with jdk support. Also have sun jre and version is 1.6.0.0 sun microsystems as shown by [http://javatester.org/version.html](http://javatester.org/version.html)

```
java -version
java version "1.6.0_0"
OpenJDK  Runtime Environment (build 1.6.0_0-b11)
OpenJDK 64-Bit Server VM (build 1.6.0_0-b11, mixed mode)

```any ideas?

---

### Post by Zill on 2009-02-10
geezerone:  Your problem *may* be due to OpenJDK or gcj.  See my post #2 above...
> Regarding java, open Synaptic package manager then

[B]Remove:
openjdk[/B]
icedtea
**gcjwebplugin**

Install:
sun-java-bin
sun-java-jre
sun-java-plugin

All the java tests in my post #5, and the BT speedtest, should then run correctly.

---

### Post by geezerone on 2009-02-10
Hi

Did see that but when I removed gcj I get message in yellow box saying no java plugin enabled or installed.

Also, sun-java-plugin isn't in repositories.

---

### Post by detroit/zero on 2009-02-10
I use a program called *vnstat *to keep track of my up/download usage. It's available in the repos```
sudo apt-get install vnstat
```You have to set up a database for your particular device once it's installed```
sudo vnstat -i ath0
```for example.

After that, by using vnstat at the terminal with the various output switches (for daily, weekly, monthly, etc..) you can get readings similar to this```
zero@zero-laptop:~$ vnstat -m

 ath0  /  monthly

   month         rx      |      tx      |   total
-------------------------+--------------+--------------------------------------
  Oct '08      40.15 GB  |     3.41 GB  |    43.57 GB   %%%%%
  Nov '08     155.44 GB  |    12.92 GB  |   168.36 GB   %%%%%%%%%%%%%%%%%%%%::
  Dec '08     138.81 GB  |    15.44 GB  |   154.25 GB   %%%%%%%%%%%%%%%%%%::
  Jan '09      85.12 GB  |    30.90 GB  |   116.02 GB   %%%%%%%%%%%::::
  Feb '09      10.56 GB  |     3.31 GB  |    13.87 GB   %
-------------------------+--------------+--------------------------------------
 estimated     29.95 GB  |     9.38 GB  |    39.33 GB
```

I personally use vnstat in my conky readout so I have all the information right at a glance
[IMG]http://img24.imageshack.us/img24/1361/screenshotsm6.png[/IMG]

---

### Post by Zill on 2009-02-10
> **geezerone said:**
> ...Also, sun-java-plugin isn't in repositories.
I suggest you check your Sofware Sources to ensure that the right repository is enabled:

Open Synaptic. Menu Settings, Repositories
Ensure line "Software restricted by copyright or legal issues (multiverse)" is checked.

Close window, then click Synaptic "Reload" button.

Type sun-java into Synaptic "Search" dialog box and sun-java5-plugin or sun-java6-plugin should be available for installation.  Install the appropriate version for your system.

---

### Post by geezerone on 2009-02-11
Thanks detroit/zero and zill. Detroit, the btspeedtester is for analysing ADSL problems in the UK.

Zill, not been on the original Ubuntu pc but another one I have doesn't have jdk, gcj or icedtea and does have sun-java-bin, sun-java-jre, sun-java-plugin installed. Different problem, in that java applet failed to load appears (red x).

Will try machine 1 at some stage but this machine 2 isn't working (different error to machine 1)

---

### Post by Zill on 2009-02-11
geezerone:  If you have sun-java-bin, sun-java-jre, sun-java-plugin all installed then my guess is that the plugin needs a symbolic link creating between /usr/lib/jvm and /usr/lib/firefox/plugins.

I can't be too specific on the exact paths as every installation can be different but I suggest you take a look in these directories and try making a symbolic link for the plugin libjavaplugin.so

Typing "about: plugins" into the Firefox address bar should show the java plugin if it is correctly linked.

---

### Post by geezerone on 2009-02-11
"about: plugins" shows:

```
**Java(TM) Plug-in 1.6.0_07-b06**

 File name:  libjavaplugin_oji.so Java(TM) Plug-in 1.6.0_07
```There is a list of java-bean applets from different versions up to the latest. Other sites are fine, just the BT site.

Cheers.

---

### Post by Zill on 2009-02-12
geezerone:  From your info it seems that Java is linked OK.  If the three test websites I gave in post #5 above are all working then it looks like the problem is with the BT site.

I never use the BT speedtester as I always use the following sites:
[URL="http://www.thinkbroadband.com/speedtest.html"]
http://www.thinkbroadband.com/speedtest.html[/URL] (java)
[URL="http://www.speedtest.net/"]
http://www.speedtest.net/[/URL] (flash)

---

### Post by geezerone on 2009-02-14
I think the btspeedtester site is fussy.

Out of interest on my first pc sun-java6-plugin isn't found in the repositories?

---

### Post by Zill on 2009-02-14
> **geezerone said:**
> ...Out of interest on my first pc sun-java6-plugin isn't found in the repositories?

I suggest you check your /etc/apt/sources.list

If an app is in the repository for one PC then then it is in for all PCs. ;-)

---

### Post by geezerone on 2009-02-15
It should be but it ain't - trust me!

---

### Post by Zill on 2009-02-15
geezerone:  The repositories shown in /etc/apt/sources.list are internet sites that contain all the relevant deb files.  As the deb files are on these internet servers, how can these vary according to which PC *you* use?

To get different listings you must be using different repositories in each /etc/apt/sources.list.

---

### Post by geezerone on 2009-02-16
Can't check the other machine now but looks like the 64bit install doesn't have that package.

---

### Post by jbruced on 2009-05-17
Sorry, wrong post

---

