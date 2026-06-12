---
title: "trying to install Brother all-in-one on ubutnu 16:04"
date: 2016-09-10
forum: Hardware
---

### Post by Timothy_Cota on 2016-09-10
I have been trying to install a Brother MFC J430W all-in-one on ubutnu 16:04.04.  I had it briefly installed once before but I can no longer find the web page where I found the Instructions.  I have tried several other sites but none work for me.  I was able to install the printer and scanner drivers with gdebi but Can't  get to the script.  I tried to install it from settings but it never finds the installed drivers, just recommends the same old generic. where do I go from here?

---

### Post by DuckHook on 2016-09-10
It would help if you linked to all the download pages and instructions that you tried to follow. Otherwise, there is no starting point with which to help.

Also describe, step-by-step, the procedure that you followed. Phrases like "Can't get to the script" are overly vague and I can't make out what you mean. It also often leads to wasting time with suggestions that you have already tried.

Please don't interpret the above as, in any way, a reproach. I know how difficult and frustrating it sometimes is wrestling with Brother drivers and I truly sympathize. But it helps to put yourself in the shoes of those you are seeking help from and then ask of yourself: what kind of info would they need to give effective advice?

---

### Post by Timothy_Cota on 2016-09-11
Thanks for the guidance.  This is going to take a long time.  I will post everything when I get it all together.     unktim

---

### Post by him610 on 2016-09-11
Please check the model number. It is not listed on the Brother support site.
[http://www.brother-usa.com/Support/Default.aspx?PGID=5&WT.svl=contact]("http://www.brother-usa.com/Support/Default.aspx?PGID=5&WT.svl=contact")

---

### Post by Timothy_Cota on 2016-09-14
My model is MFC J430W.  It is listed and I have found it several times.  As I stated I had this machine installed on 16:04 once before, but I had some serious issues with  16:04 and went back to 14:04 and then upgraded.  I was able to install my epson as a printer only.  I was able to download and install the brother printer and Iscan  packages with gdebi but am at a loss as to what to do from here.

---

### Post by SeijiSensei on 2016-09-15
Go back to the Brother site and download the "[driver install tool]("http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfcj430w_all&os=128")."  Run that from the command prompt as root with sudo.  It should download the required drivers and install them for you.

---

### Post by Bucky Ball on 2016-09-15
> **SeijiSensei said:**
> Go back to the Brother site and download the "[driver install tool]("http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfcj430w_all&os=128")."  Run that from the command prompt as root with sudo.  It should download the required drivers and install them for you.

That is all you should need to do. If you're doing it any other way, which it sounds like you are as it's going to take you awhile to get together what you've tried to tell us,  you're doing it wrong. :) 

Follow the instructions on the linked site. Should be done in five minutes. Of course, you may need to revert whatever it is you've done to get it to work as you may have caused other issues, but see how you go.

The instructions on how to use the driver install tool are on the page you get to when you agree to the EULA.

---

### Post by DuckHook on 2016-09-15
It is best to follow SeijiSensei's advice first and just use the driver install tool. However, a few Brother models require the following fix (though I am not sure that yours does): [http://askubuntu.com/questions/47881/brother-mfc-295cn-scanner/48389#48389](http://askubuntu.com/questions/47881/brother-mfc-295cn-scanner/48389#48389)

This is an obscure requirement mainly for older/cheaper Brother models. It was the missing ingredient in a really cussed scanner install that I was trying to get working for a relative. Do not monkey with the /lib/udev/rules.d/40-libsane.rules file until you've tried a simple install using the driver install tool first. But if it doesn't work, then make a copy of the above file under another name (for ease of reversion if necessary), then (using an editor) add the entries outlined in the link, save and reboot.

Purely as an aside: the need for obscure fixes like this are one of the reasons that I don't recommend Brother equipment for Ubuntu. Most Brother products appear to just work once the driver is installed, but all too often, a nasty problem like this one crops up.

---

### Post by Bucky Ball on 2016-09-15
> **DuckHook said:**
> Purely as an aside: the need for obscure fixes like this are one of the reasons that I don't recommend Brother equipment for Ubuntu. Most Brother products appear to just work once the driver is installed, but all too often, a nasty problem like this one crops up.

Strange how it goes. Never had an issue and am, in fact, about to buy a new Brother later today or tomorrow. Then again, I tend to research the living daylights (sometimes spending days, weeks) out of any hardware purchases I make for Ubuntu before parting with the cash ...

(I built this computer I am using in February and I researched the build on and off for ... five months? then fairly solidly for about a month. Suffice to say, it works great. It's 16.04 that has some odd glitches which is confirmed by having odd glitches with it on my and my wife's laptops also.)

---

### Post by DuckHook on 2016-09-15
> **Bucky Ball said:**
> …Then again, I tend to research the living daylights (sometimes spending days, weeks) out of any hardware purchases I make for Ubuntu before parting with the cash ...…and *that* is the secret sauce in your successful recipe. Proper preparation tends to make everything go far smoother.

---

### Post by Timothy_Cota on 2016-09-15
unfortunately, I owned the printer long before I installed ubuntu.  unktim

---

### Post by DuckHook on 2016-09-15
> **Timothy_Cota said:**
> unfortunately, I owned the printer long before I installed ubuntu.  unktimOf course. I was just referring to new purchases (other readers&#8213;who may be considering new purchases&#8213;see this thread on the forums too).

For existing MFCs, the instructions already posted can be tried.

---

### Post by kurt18947 on 2016-09-15
SWMBO has this very machine. The installer script should do what needs to be done without manually editing any files on 16.04. One function I haven't tested is printing and scanning over a wireless network.

---

### Post by DuckHook on 2016-09-15
> **kurt18947 said:**
> SWMBO has this very machine. The installer script should do what needs to be done without manually editing any files on 16.04. One function I haven't tested is printing and scanning over a wireless network.…that is good news, then.

@ Timothy_Cota

Try the installer script that a number of posters have already pointed to. SeijiSensei has already provided the link.

---

### Post by Timothy_Cota on 2016-09-15
Okay guys. I am throwing in the towel.  I have tried everything everybody has told me to including downloading the install tool for the fifth time.  the first three times I used gdebi.  Each time I got a message:  "This is not a Debian package but a mime."  The last two times I downloaded it to my home folder and tried to install it from the command line.  Answer I get is "package not found".  I think I need to go back and learn terminal commands an some bash basics.
As I look over my threads I can see that I have cost a lot of people a lot of time and for that I apologize.  unktim

---

### Post by DuckHook on 2016-09-15
> **Timothy_Cota said:**
> Okay guys. I am throwing in the towel.I am saddened by this result. Would have like to have helped.> &#8230;I have cost a lot of people a lot of time and for that I apologize.Good gracious&#8230; please don't feel that way. We are happy to help or at least give it the ol' college try, so no need to apologize. If you change your mind, we are still here to help.

FWIW, should you decide to purchase a new MFC, I would suggest something from HP. In fact, a slightly older HP model would be perfect. The HP products tend to be the best-supported in Linux and their Linux support group produces a fine management tool called *hplip* that is included as a standard tool in every default install.

---

### Post by wagb278 on 2016-09-15
Not sure this will help you, but...
I got a neighbor to switch to using Ubuntu MATE-14.04 a few years ago and had problems getting the Brother multi-function printer (model MFC-J870DW) to connect. My problem turned out to be misunderstanding how to answer the questions asked by the installation script.  The neighbor has the printer connected via Ethernet to the router and the printer has a static IP assigned.  The wireless feature is not in use at this time.

If the test page does not print near the end of running the installer script, access the CUPS control page via a web browser (localhost:631) and click on the Printers Tab to list the installed printers.  Click on your Brother printer's queue name to access that specific printer.  Look at the Connection entry.

If the Connection says: lpd://BRN<mac address>/BINARY_P1 one more change is needed.  That BRN<mac address> string needs to be either changed to the printer's IP Address or add an entry in the file /etc/hosts.  Either option should work. If using the /etc/hosts file option just add an entry that associates the printer's IP address with the BRN<mac address> string.

That solved the issue for my neighbor's Brother printer and scanner.  Printing works as usual and Simple Scan application works for scanning.  Not sure the document feeder for scanning works because we didn't text that. To my knowledge my neighbor has not upgraded to 16.04 yet.

---

### Post by Bucky Ball on 2016-09-15
I think your issue is that you're not issuing the commands in the directory you have the installer downloaded to. If it is in /home/user/downloads, for instance, you need to do

```
cd /home/user/downloads
```

... to get into the directory where you downloaded the file, then the commands given on the Brother page. (You will need to change the path to the file directory to suit your details, of course.) 

Once you're in that directory, to have a look at what files are in it, type:

```
dir
```

... and hit enter. You should see the file you downloaded listed there.

That's about it. Looks like you're almost there but for a couple of steps. No point in downloading the driver tool over and over again, incidentally. Not going to change things. It's how you're going about installing.

If you do manage to get it installed, go to 'Printers', 'Add Printer' and follow your nose. When asked to select a driver, select Brother> your driver will be available in the next list.

Anyhow, just throwing that in in case you decide to retract the towel for one more try ... :)

PS: You haven't wasted anyone's time. Our goal is to get your problem fixed and there's a lot of persistent folk around this joint! :)

---

### Post by SeijiSensei on 2016-09-15
> **Timothy_Cota said:**
> Okay guys. I am throwing in the towel.  I have tried everything everybody has told me to including downloading the install tool for the fifth time.  the first three times I used gdebi.  Each time I got a message:  "This is not a Debian package but a mime."  The last two times I downloaded it to my home folder and tried to install it from the command line.  Answer I get is "package not found".  I think I need to go back and learn terminal commands an some bash basics.
As I look over my threads I can see that I have cost a lot of people a lot of time and for that I apologize.  unktim
None of those problems are insurmountable.

First stop fussing with gdebi and just use the install tool.

Next, the file you download will be called "linux-brprinter-installer-2.0.0-1.gz".  That's compressed using gzip, so you first have to unzip it like this
```
$ gunzip linux-brprinter-installer-2.0.0-1.gz
```.
Now you will have a file called "linux-brprinter-installer-2.0.0-1".  However it cannot be run unless you first make it executable.  So next issue the command:
```
$ chmod a+x linux-brprinter-installer-2.0.0-1
```

Now you're almost done. If the script resides in the current directory, you must use "./" to run the script like this:

```
$ sudo ./linux-brprinter-installer-2.0.0-1
```

How does that work for you?

---

### Post by Bucky Ball on 2016-09-15
An even better description, a step-by-step. Nice one, SeijiSensei. :)

---

### Post by Timothy_Cota on 2016-09-15
This is as far as I got: 
unktim@melvin:~$ cd /home/user/downloads
bash: cd: /home/user/downloads: No such file or directory
unktim@melvin:~$

---

### Post by Bucky Ball on 2016-09-15
As I said, you need to replace those details with the details for your machine. You are going have nothing at /home/user/downloads, no.

Open a filemanager, navigate to where you downloaded the driver. Mine would be at:

/home/bucky/Downloads/

... and the file is in that directory. Where is yours? It will NOT be in the same place as mine. Wherever it is, open a terminal and 'cd' (change directory) to that directory. For example, using MY details, not yours because I have no idea of them:

```
cd /home/bucky/Downloads
```

... then:

```
dir
```

Your driver should be there. Follow Brother instructions. 

Please read posts carefully so you don't miss these details when people are posting help. It will save time, effort and redundancy. :)

Good luck.

---

### Post by SeijiSensei on 2016-09-15
It should be in /home/unktim/Downloads.  Remember, too, that Linux is case sensitive.  /home/unktim/downloads is not the same as /home/unktim/Downloads.

---

### Post by Timothy_Cota on 2016-09-16
Again, thanks to everybody who helped.   unktim

---

### Post by Timothy_Cota on 2016-09-18
Update:  I think that a big part of my problem was that I was running a 64 bit ubuntu  on a 32 bit computer.  I installed win 7 and partitioned the hard drive to run side-by-sides.  Then I downloaded a 32 bit iso image of ubuntu 12:04.5 and installed it.  It runs beautifully and I was able install my epson al-in-one without difficulty.  I tried running a few basic commands in terminal and they worked for the first time.  I still can't install my wife's brother all-in-one but I installed it on win 7.  Someday after I learn enough I will try it again.
On again I thank everyone who helped.  It probably won,t be long before I have another problem.   unktim

---

### Post by Bucky Ball on 2016-09-18
A 64bit version of Ubuntu would not install on a 32bit machine as far as I know.

Two things: 

Why are you using 12.04 and not something newer? Any reason? 
Whether you are using 32 or 64bit OS should make no difference to the Brother driver.

Then again, perhaps you just didn't have the 32bit stuff required in your 64bit install to deal with the drivers, it the driver is 32bit only. :-k

Thanks for marking as solved.

---

