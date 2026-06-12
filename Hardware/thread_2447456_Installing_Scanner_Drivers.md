---
title: "Installing Scanner Drivers"
date: 2020-07-19
forum: Hardware
---

### Post by daniell59 on 2020-07-19
This has always been my nemesis. Every time I upgrade Ubuntu, I have great difficulty installing the scanner drivers. I found a package that is supposed to support Ubuntu 20.04. Maybe it is too much for my 73 year old brain. The image will show what I have done so far. 

OS Ubuntu 20.04

Scanner Epson Perfection V30

Thanks in Advance.

---

### Post by rbmorse on 2020-07-19
From a terminal:

cd Downloads
chmod +x install.sh
sudo ./install.sh

---

### Post by daniell59 on 2020-07-19
> **rbmorse said:**
> From a terminal:

cd Downloads
chmod+x install.sh
sudo ./install.sh

When I type chmod+x install.sh it says command not found.

---

### Post by pqwoerituytrueiwoq on 2020-07-19
missing space "chmod +x"

---

### Post by daniell59 on 2020-07-19
daniel@daniel-P5Q-PRO:~$ cd downloads
bash: cd: downloads: No such file or directory
daniel@daniel-P5Q-PRO:~$ cd Downloads
daniel@daniel-P5Q-PRO:~/Downloads$ chmod+x install.sh
chmod+x: command not found
daniel@daniel-P5Q-PRO:~/Downloads$ chmod +x
chmod: missing operand after ‘+x’
Try 'chmod --help' for more information.
daniel@daniel-P5Q-PRO:~/Downloads$ chmod +x
chmod: missing operand after ‘+x’
Try 'chmod --help' for more information.
daniel@daniel-P5Q-PRO:~/Downloads$

---

### Post by pqwoerituytrueiwoq on 2020-07-19
this is the full line:
"chmod +x install.sh"
i was just pointing out where the issue was in the instructions you were given

---

### Post by daniell59 on 2020-07-19
> **pqwoerituytrueiwoq said:**
> this is the full line:
"chmod +x install.sh"
i was just pointing out where the issue was in the instructions you were given

Thanks, but I must be missing something

Command 'hmod' not found, did you mean:

  command 'qmod' from deb gridengine-client (8.1.9+dfsg-9build2)
  command 'chmod' from deb coreutils (8.30-3ubuntu2)
  command 'mod' from deb monodoc-base (6.8.0.105+dfsg-2)
  command 'kmod' from deb kmod (27-1ubuntu2)
  command 'jmod' from deb openjdk-11-jdk-headless (11.0.7+10-3ubuntu1)
  command 'jmod' from deb openjdk-13-jdk-headless (13.0.3+3-1ubuntu2)
  command 'jmod' from deb openjdk-14-jdk-headless (14.0.1+7-1ubuntu1)

Try: sudo apt install <deb name>

---

### Post by rbmorse on 2020-07-19
> **pqwoerituytrueiwoq said:**
> missing space "chmod +x"

I hate it when I do that.  Thanks!

---

### Post by rbmorse on 2020-07-19
> **daniell59 said:**
> Thanks, but I must be missing something

Command 'hmod' not found, did you mean:

  command 'qmod' from deb gridengine-client (8.1.9+dfsg-9build2)
  command 'chmod' from deb coreutils (8.30-3ubuntu2)
  command 'mod' from deb monodoc-base (6.8.0.105+dfsg-2)
  command 'kmod' from deb kmod (27-1ubuntu2)
  command 'jmod' from deb openjdk-11-jdk-headless (11.0.7+10-3ubuntu1)
  command 'jmod' from deb openjdk-13-jdk-headless (13.0.3+3-1ubuntu2)
  command 'jmod' from deb openjdk-14-jdk-headless (14.0.1+7-1ubuntu1)

Try: sudo apt install <deb name>

You made a typo (lots of that going around, today).  Try it again.

---

### Post by daniell59 on 2020-07-19
I am still open to assistance.

---

### Post by rbmorse on 2020-07-19
Lets try this.  Using the file browser, open the Downloads folder.  

Right click on the file install.sh.  

Click on "properties" at the bottom of the pop-up. 

Click on the Permissions tab.  That will open a new popup window. 

Left click on the box "Allow executing file as program" on the Execute: line.  A checkmark should appear in the box. 

Close that window

Close or minimize the file manager window

open the terminal

change to the Downloads folder with the command:   cd Downloads

verify you're in the right place with the command  : ls    (that's a lower case letter "L")

you should see the files and folders from the driver package you downloaded and unpacked.  The file "install.sh" (no quotes) should be one of them.   

IF you see the file "install.sh" in the list returned by the "ls" command, run the script with the command:

```
sudo ./install.sh
```

---

### Post by pqwoerituytrueiwoq on 2020-07-19
> **daniell59 said:**
> Thanks, but I must be missing something

Command 'hmod' not found, did you mean:

  command 'qmod' from deb gridengine-client (8.1.9+dfsg-9build2)
  command 'chmod' from deb coreutils (8.30-3ubuntu2)
  command 'mod' from deb monodoc-base (6.8.0.105+dfsg-2)
  command 'kmod' from deb kmod (27-1ubuntu2)
  command 'jmod' from deb openjdk-11-jdk-headless (11.0.7+10-3ubuntu1)
  command 'jmod' from deb openjdk-13-jdk-headless (13.0.3+3-1ubuntu2)
  command 'jmod' from deb openjdk-14-jdk-headless (14.0.1+7-1ubuntu1)

Try: sudo apt install <deb name>
when you copy/pasted you missed the 1st letter

---

### Post by daniell59 on 2020-07-20
I do appreciate your help. I don't see where I missed a letter while copying and pasting. I am ashamed to say that I am somewhat confused. I guess I need to be walked through. Thanks again for the effort that you made on my behalf.

---

### Post by pqwoerituytrueiwoq on 2020-07-20
you want it to look something like this
[img]https://imgur.com/oGyi9on.png[/img]
you missed the starting letter 'c' in the name 'chmod' which is why you got the error "Command 'hmod' not found"
If you can't see that I'm sorry i do not know how to help you without doing it for you in person

---

### Post by daniell59 on 2020-07-20
I don't know whether this will help. This is in my Downloads 

daniel@daniel-P5Q-PRO:~/Downloads$ cd Downloads
bash: cd: Downloads: No such file or directory
daniel@daniel-P5Q-PRO:~/Downloads$ dir
c05105530.pdf
hplip-3.20.6.run
imagescan-bundle-ubuntu-20.04-3.63.0.x64\ (1).deb
imagescan-bundle-ubuntu-20.04-3.63.0.x64.deb
imagescan-bundle-ubuntu-20.04-3.63.0.x64.deb.tar.gz
install.sh
daniel@daniel-P5Q-PRO:~/Downloads$ 

As before, thanks for your time and effort. I did not expect to get this working for a while. I still have it working on my other computer that has Ubuntu 16.04.

---

### Post by rbmorse on 2020-07-20
[B]ignore this post and see the next one.  I just noticed [COLOR=#000000][FONT=&amp]imagescan-bundle-ubuntu-20.04-3.63.0.x64.deb is a directory, not a file.  Jeebuz. [/FONT][/COLOR]
[/B]

---

### Post by rbmorse on 2020-07-20
I just realized I committed a grevious error in the last post. Apologies for any confusion. 

To pick things up again. 

Using the terminal, and starting in the Downloads directory again (where you were in your last post). 

type the command:

```
cd imagescan-bundle-ubuntu-20.04-3.63.0.x64.deb
```

type the command ```
ls
```

that should produce the output:

```
core  install.sh  plugins  README.rst
```

If that's the case, and just to verify things, please run the command:

```
./install.sh --dry-run
```

that should produce the output:

```
 apt-get update apt-get install --assume-yes libboost-program-options1.71.0 libgraphicsmagick++-q16-12 libgtkmm-2.4-1v5 graphicsmagick
dpkg --install ./core/imagescan_3.63.0-1epson4ubuntu20.04_amd64.deb ./plugins/imagescan-plugin-networkscan_1.1.3-1epson4ubuntu20.04_amd64.deb ./plugins/imagescan-plugin-gt-s650_1.0.2-1epson4ubuntu20.04_amd64.deb ./plugins/imagescan-plugin-ocr-engine_1.0.2-1epson4ubuntu20.04_amd64.deb

```

All that did was show what the install.sh command is going to do when executed for real.  So now, if that is what happened on your machine and if the gods are smiling on us, the next step should install the drivers:

```
sudo ./install.sh
```   

That should be all you have to do. I just did these exact steps on my machine and it worked fine, although I no longer have a V30 scanner to test it with.

---

### Post by daniell59 on 2020-07-21
[email]daniel@daniel-P5Q-PRO:~/Downloads/imagescan-bundle-ubuntu-20.04-3.63.0.x64.deb[/email]$ cd imagescan-bundle-ubuntu-20.04-3.63.0.x64.deb
bash: cd: imagescan-bundle-ubuntu-20.04-3.63.0.x64.deb: No such file or directory
[email]daniel@daniel-P5Q-PRO:~/Downloads/imagescan-bundle-ubuntu-20.04-3.63.0.x64.deb[/email]$  
  
No celebration yet

---

### Post by rbmorse on 2020-07-21
Nope, it didn't work because you didn't start in the right place.  

I'd like you to try it again, but this time before you start open the Terminal application and note the prompt. It should look like:

```
daniel@daniel-PQ5-PRO:~$
```

On my terminal the username/machine name is in green, the colon is white, the tilde is blue and the dollar sign is white, but that doesn't matter for now.  if the prompt shows something else (other than the colors), enter the command:

```
cd /home/daniel
```

Once the prompt is correct, enter the command:

```
cd Downloads
```

Now the prompt should look like:

```
daniel@daniel-PQ5-PRO:~/Downloads$
```

now, _IF_ that's the case, go back to #17 above and pick it up at the top.  Otherwise we have to get you to the right place or the process will fail again.

---

### Post by daniell59 on 2020-07-21
daniel@daniel-P5Q-PRO:~$ cd Downloads
daniel@daniel-P5Q-PRO:~/Downloads$ cd imagescan-bundle-ubuntu-20.04-3.63.0.x64.deb
[email]daniel@daniel-P5Q-PRO:~/Downloads/imagescan-bundle-ubuntu-20.04-3.63.0.x64.deb[/email]$ ls
core  install.sh  plugins  README.rst
[email]daniel@daniel-P5Q-PRO:~/Downloads/imagescan-bundle-ubuntu-20.04-3.63.0.x64.deb[/email]$ ./install.sh
internal error: unsupported package format
[email]daniel@daniel-P5Q-PRO:~/Downloads/imagescan-bundle-ubuntu-20.04-3.63.0.x64.deb[/email]$  

Sorry, I am not there yet.

---

### Post by rbmorse on 2020-07-21
no, that won't do it.  At the point where the list of instructions failed, there were two commands you could have run, but you did something else. 

I asked that you run the command:

```
./install.sh --dry-run
```

This is an error check.  Please run it from the ~/Downloads/imagescan-bundle-ubuntu-20.04-3.63.0.x64.deb directory.  Did that produce the output shown above in #17?  If not, what did it tell you? 

Also, if not, what is the output of the command:

```
ls /usr/bin/sh
```

should be /usr/bin/sh

---

### Post by daniell59 on 2020-07-21
I am really sorry to be so troublesome. Maybe I am missing something. I understand if you don't want to put anymore time into this. I do appreciate the effort that you made on my behalf.

daniel@daniel-P5Q-PRO:~$ cd Downloads
daniel@daniel-P5Q-PRO:~/Downloads$ cd imagescan-bundle-ubuntu-20.04-3.63.0.x64.deb
[email]daniel@daniel-P5Q-PRO:~/Downloads/imagescan-bundle-ubuntu-20.04-3.63.0.x64.deb[/email]$ ls
core  install.sh  plugins  README.rst
[email]daniel@daniel-P5Q-PRO:~/Downloads/imagescan-bundle-ubuntu-20.04-3.63.0.x64.deb[/email]$ ./install.sh --dry-run
internal error: unsupported package format
[email]daniel@daniel-P5Q-PRO:~/Downloads/imagescan-bundle-ubuntu-20.04-3.63.0.x64.deb[/email]$

---

### Post by rbmorse on 2020-07-21
Naw...this is more fun than plucking chickens or learning to speak Mandarin. Apologies if my last came across as a bit terse.  

In any case, the error message you received is internal to the script itself, not something you did.  You may have a bad download from Epson.  I can tell you I ran the script on my machine and it worked, so the next step is normally to download the package again an see if that makes a difference. So let's try that. 

First, life is going to be easier if you empty everything currently in your Downloads directory.  So do that.  If there is anything there from another project you want to keep, move it somewhere safe. 

Once the Downloads folder is empty, start your Internet browser and navigate to:

[http://support.epson.net/linux/en/imagescanv3.php#ubuntu](http://support.epson.net/linux/en/imagescanv3.php#ubuntu)

In the Ubuntu section, find the entry:

 Ubuntu 20.04(LTS)   64bit(amd64)  

and click on the download button at the end of that line.  That should download the full driver package
with the name: 

```
[COLOR=#000000]Imagescan-bundle-ubuntu-20.04-3.63.0.x64.deb.tar.gz[/COLOR]
```

[COLOR=#000000]Close the Internet browser window and open the file browser.  Navigate to your Downloads directory (/home/daniel/Downloads). [/COLOR]
[COLOR=#000000]You should now see only the driver package, and nothing else.  If that's not the case, stop and fix that before going any further. [/COLOR]
[COLOR=#000000]
Next, right click on the driver package. That will open a popup window.  In that window, click on "extract here".[/COLOR]

[COLOR=#000000]When that's done, you should see two items in your file browser window: The driver package with the name:[/COLOR]

```
[COLOR=#000000]imagescan-bundle-ubuntu-20.04-3.63.0.x64.deb.tar.gz [/COLOR]
```[COLOR=#000000]

and a new folder with the name:

[/COLOR]```
[COLOR=#000000]imagescan-bundle-ubuntu-20.04-3.63.0.x64.deb[/COLOR]
```

[COLOR=#000000]Double click on the *_folder_ *[/COLOR][COLOR=#000000]imagescan-bundle-ubuntu-20.04-3.63.0.x64.deb. 

That will open a new window with four items in it; two folders (core and plugins) and two files (install.sh and README.rst)

***** marker for future reference *****

Now, we're going to skip a lot of monkey motion because when I did this on my machine it just worked.  The readme file says this should just work, so
you're going to do this now and it will just work. 

open a terminal and change to the Downloads folder with the command:

```
cd Downloads
```

verify you're in the right place by checking the content of the folder with the ls (list) command:

```
ls
```

You should see the driver package [/COLOR][COLOR=#000000]imagescan-bundle-ubuntu-20.04-3.63.0.x64.deb.tar.gz and the extracted folder [/COLOR][COLOR=#000000]imagescan-bundle-ubuntu-20.04-3.63.0.x64.deb. Nothing else.  If that's the case, enter the command:

```
cd ima<tab>
```  (where <tab> means press the tab key) That will expand the command to the full name of the directory without having to type the whole thing, and minimize the chance of typos.  Press the <enter> key. 

Again, verify we're in the right place with the ls command.  This time you should see the two folders (code and plugins) and two files (install.sh and README.rst) mentioned above. 

Take a deep breath and run the command:

```
./install.sh --dry-run
```

On my machine this is the output I get:

[/COLOR]```
dpkg --install ./core/imagescan_3.63.0-1epson4ubuntu20.04_amd64.deb ./plugins/imagescan-plugin-networkscan_1.1.3-1epson4ubuntu20.04_amd64.deb ./plugins/imagescan-plugin-gt-s650_1.0.2-1epson4ubuntu20.04_amd64.deb ./plugins/imagescan-plugin-ocr-engine_1.0.2-1epson4ubuntu20.04_amd64.deb
```[COLOR=#000000]

If you get something else, like that unsupported package format error from before, stop and let me know.  Otherwise, now is the time to just go for it:

```
./install.sh
```  

In looking at the script, it should not be necessary to use the sudo prepend to run this command or manually set the execute bit in permissions. The script should ask you for your user password and then take care of things.  However, if you get a permissions error, try it again with the sudo prepend:

```
sudo ./install.sh
```

let me know how you do. If _this_ doesn't work, I have a plan "B". 

[/COLOR][COLOR=#000000]

 

[/COLOR][COLOR=#000000]



[/COLOR]

---

### Post by Kris_M on 2020-07-21
lately I find ignoring the scanner driver and using simple-scan helps. Maybe also install xsane.

---

### Post by rbmorse on 2020-07-21
Those are both good ideas, but he's got an Epson V30 that needs a proprietary driver plugin and a couple other slimy bits from the Epson imagescan application first. I fought one of these for years and never found a way around the installer...until today, but I want to see how Daniel does with a fresh download package. I think is last one was borked.

---

### Post by daniell59 on 2020-07-22
Again I am ashamed to post this.

daniel@daniel-P5Q-PRO:~$ cd Downloads
daniel@daniel-P5Q-PRO:~/Downloads$ ls
imagescan-bundle-ubuntu-20.04-3.63.0.x64.deb
imagescan-bundle-ubuntu-20.04-3.63.0.x64.deb.tar.gz
daniel@daniel-P5Q-PRO:~/Downloads$ cd ima<tab>
bash: syntax error near unexpected token `newline'
daniel@daniel-P5Q-PRO:~/Downloads$

---

### Post by rbmorse on 2020-07-22
Don't be ashamed.  Every new error represents progress...of a sort. But, it looks like there's a missing package or configuration error with your machine. No worry, we'll work around it.  But first, open the terminal and type the command:

```
ls /usr/bin/sh
```

it should simply return the result : /usr/bin/sh

Is this what happens? 

There is an alternative way to do this, but I need to do a little more testing and research so it will take a bit to write up. Plus the dogs need some attention this morning and Border Collies will not be denied, so it will be a couple of hours before I can get it up.  We'll get this.

---

### Post by daniell59 on 2020-07-22
daniel@daniel-P5Q-PRO:~$ ls /usr/bin/sh

---

### Post by rbmorse on 2020-07-22
Great. That command should have returned the result

/usr/bin/sh

But that's for later. No idea why terminal didn't expand the directory name, but that's for later, too. 

So....this is plan "B".  Probably should have done this earlier. gdebi is a GUI accessory tool that 
allows point and click manipulation of .deb packages. It just makes things a bit easier.  It's in
the Ubuntu file repository so we don't have to worry about safety.  Install it as follows: 

Open a terminal and enter the command:

```
sudo apt install gdebi
``` 

enter your user password when prompted.  There will be some monkey motion that follows. [B]If you receive an 
error message, stop[/B] and let me know what it says.  There should be no error messages. If you see a result that says 
something like "gedbi is already the newest version" that's OK.  Press on. 

Close the terminal window.  We won't need it anymore. 

Open the file browser, and navigate to the Downloads folder.  You should see two objects:  

imagescan-bundle-ubuntu-20.04-3.63.0.x64.deb
imagescan-bundle-ubuntu-20.04-3.63.0.x64.deb.tar.gz

Double click on the imagescan.....deb folder.  You should now see two folders (core and plugin) and two files (.install.sh and README.rst)

Right click on the core folder.  It contains one file named: imagescan_3.63.0-1epson4ubuntu20.04_amd64.deb

right click on that file.  A new popup window will open. The first item should be "open with gedbi package installer".  Left click on that. 

A new window will popup.  

Check the "status" line and make sure it says "all dependencies are satisfied".  if not,** stop** and let me know what the status says 
because we have to fix it before the package will install.  

If all dependencies are satisfied, click on the "install package" button.   Enter your user password when prompted. The package will install. Or report errors. 

The status will change to "Same version is already installed" to indicates the package installed successfully.  

Close the gdebi popup.  

Navigate to the ~/Downloads/imagescan...deb folder

Double click on the plugins folder.  You'll see three .deb packages. 

You probably only need the imagescan-plugin-gt-s650_1.0.2-1epson4ubuntu20.04_amd64.deb package. 
 
We're going to install it with gdebi the same way we did the imagescan package. 

Same sequence:

Right click on imagescan-plugin-gt-s650_1.0.2-1epson4ubuntu20.04_amd64.deb
click on "open with gdebi"
verify status as "all dependencies are satisfied"
click install button
enter password when prompted
verify status as "same version already installed"
close gdebi popup

The other two packages appear to be optional.  If you access your scanner over a network, install the 
imagescan-plugin-networkscan...deb package in the same way as the other two.  

The ...ocr_engine...deb appears to be a work in progress.  If you need to do ocr work go ahead and 
install it in the same way as the others. 

close the file browser window. Fini. Almost. 

Make sure the scanner is connected and powered.  Open the activities window and look for the Image 
Scan icon.  Double click on it to start the application. If the status box at the upper left shows 
"no devices found" don't panic, just close everything and reboot.  

When the machine comes back up, login normally and open the Image Scan application. This time the 
scanner should appear in the status box. If not let me know and we'll start troubleshooting.

Good luck!

---

### Post by michael-hi on 2020-07-22
Sorry to intrude so belatedly on an already lengthy thread, but I suspect where the OP went wrong in his last attempt was he probably literally typed **cd ima<tab>** instead of typing **cd ima** and then pressing the tab key.

The other thing is I wonder if this is the right driver anyway (a bit late to say this, I know!). If you go to the Epson download page:

[http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)

and input **Perfection V30** you are pointed to an older iscan driver and not the imagescan v3 driver???

---

### Post by rbmorse on 2020-07-22
I was wondering about the <tab> business, too. The next line mentions that <tab> means press the tab key, but he may have missed it. Daniel? In any case I'll remember for future reference the correct way to do things is to explain the notation _before_ listing the command.  Thank you for the reminder. 

The older V30 package predates Ubuntu 20.04.  The new version contains the required plugin for the V30 and should support his scanner, but I'm holding the older version in reserve.  It does install for me on my 20.04, but Daniel may have some configuration issue I don't.

---

### Post by daniell59 on 2020-07-25
I went to the Vuescan sight and downloaded their software for a trial. The scanner was not detected. I contacted the company. They said that I would first have to go to the Epson site and download their drivers for Linux. If I could have done that, I would not need them. I may be a heretic, but on my next build, I will have a dual boot with the scanner living on Windows 10.

---

### Post by rbmorse on 2020-07-25
I gather using gdebi to install the .deb files directly did not work for you.  

I have a feeling the problem is just a small thing; the Epson driver package installs fine here.  Still, I understand that this can be a frustrating exeprience.

Send me a Private message with a phone number and a good time to contact you if you'd like to try it that way.

---

