---
title: "How to Install HL-2140 Driver on Ubuntu 14.04+"
date: 2014-06-25
forum: Hardware
---

### Post by GreenRaccoon on 2014-06-25
lpadmin -p 'name' -E -v 'address' -P '/path/to/ppd_file'lpinfo -vOk guys, I'd like to make a thread to prevent other people from having the headaches I've had trying to set up this printer.

[COLOR=#ff0000]***On OLDER versions of Ubuntu, the method is different.***[/COLOR] That's why it was so hard for me to figure out. For older versions, you need to change the print driver from "[COLOR=#0000ff]Brother HL-2140 Foomatic/Postscript [en] (recommended)[/COLOR]" to "[COLOR=#0000ff]Brother HL-2140 Foomatic/hpijs-pcl5e [en][/COLOR]". For Ubuntu 14.04 (and probably later versions too), you need to change the driver to "[COLOR=#0000ff]Brother HL-2140 Foomatic/hl1250 [en][/COLOR]".

I'm using 64-bit, so this will probably work for 32-bit too.

_For Ubuntu 14.04 (and probably later versions too):_
1- **Plug in the printer through USB**. If your printer is already added, skip ahead to step 8.
2- **Go to "Printers"** (under "System Settings")
3- **Click "[COLOR=#006400]Add[/COLOR]"**
4- **Choose "[COLOR=#0000ff]Brother HL-2140 (*********)[/COLOR]"** The *'s are just your serial number, so ignore them. The Description will say "A printer connected to a USB port."
5- **Click "[COLOR=#006400]Forward[/COLOR]"**
6- You can change the name and description of your printer if you want; it's just the name you'll see when you go to print something later on. If you're like me and don't care, just leave it how it is. Once you're done, **click "[COLOR=#006400]Apply[/COLOR]"**.
7- **Click "[COLOR=#006400]Cancel[/COLOR]"** (the test page won't work)
8- **Right click your printer and go to "[COLOR=#0000ff]Properties[/COLOR]"**
9- Look for "Make and Model:" and then **click "[COLOR=#0000ff]Change...[/COLOR]"**
10- Let it search.
11- Once "[COLOR=#0000ff]Brother (recommended)[/COLOR]" is highlighted, **click "[COLOR=#006400]Forward[/COLOR]"**.
12- **[COLOR=#ff0000]*This is the important part.*[/COLOR]** Under "Drivers", what's highlighted is "Brother HL-2140 Foomatic/Postscript [en] (recommended)". Lies!!! **Click this driver instead [COLOR=#0000ff]"Brother HL-2140 Foomatic/hl1250 [en][/COLOR]"**.
13- **Click "[COLOR=#006400]Forward[/COLOR]"**
14- I'm guessing either option would work. If you want to choose the safer option, **choose the first option: "[COLOR=#0000ff]Use the new PPD (Postscript Printer Description) as is[/COLOR]"**. You'll just have to change your default print settings later, which isn't a big deal.
15- **Click "[COLOR=#006400]Apply[/COLOR]"**
16- **Click "Ok"**
17- You have a new Brother. Now he'll do whatever you ask him to. Make him your paper slave.
[COLOR=#000000][FONT=Sorts Mill Goudy][HR][/HR][/FONT][/COLOR]If the above option didn't work for you, here's another option. (You might need to run "apt-get install curl" first.)
1- **Plug in the printer through USB**. 
2- **Download** the **ppd**  for your printer. *(If these commands don't work, go to [this page]("https://www.openprinting.org/printer/Brother/Brother-HL-2140"), find the recommended driver, and click "Directly Download PPD".)*
```
cd ~/Downloads
curl -o "hl2140.ppd" 'https://www.openprinting.org/ppd-o-matic.php?driver=hpijs-pcl5e&printer=Brother-HL-2140&show=0'
```
3- **Find **the **address** of your printer with this command (it will start with "[COLOR=#008000]direct usb://[/COLOR]").
```
sudo lpinfo -v
```4- **Add **your **printer** by using the **ppd** you just downloaded:
```
sudo lpadmin -p 'name' -E -v 'address' -P "$HOME/Downloads/hl2140.ppd"
```

[LIST]
[*]Replace '[COLOR=#0000ff]name[/COLOR]' with whatever you want your printer to be called (e.g. '[COLOR=#800080]Brother-HL-2140[/COLOR]').
[*]Replace '[COLOR=#0000ff]address[/COLOR]' with the address you found in step 3. Make sure you DON'T include the "[COLOR=#b22222]direct[/COLOR]" part, just the "[COLOR=#008000]usb://[/COLOR]" part. (e.g. '[COLOR=#800080]usb://Brother/HL-2140%20series?serial=123456789[/COLOR]')
[/LIST]
5- (optional) **Check** that it worked:
```
sudo lpstat -p
```

---

### Post by bigonegotaway2 on 2014-07-04
[SIZE=3][COLOR=#ff0000]**Excellent Instructions **[/COLOR][/SIZE]- This is exactly how to make your Brother work for you!  i'm running a 32 bit system and yes, it works just great!  ;)

---

### Post by GreenRaccoon on 2014-07-04
Awesome. Glad I could help!

---

### Post by pepper3 on 2015-03-16
> **GreenRaccoon said:**
> Awesome. Glad I could help!

THanks man!  You are a life-saver!  

I wasted over an hour of my time reading an old out-dated guide but your instructions (In the first paragraph) did the trick

Confirmed on Kubuntu 14.04 64 bit as well as Peppermint OS 5 64 bit

---

### Post by mail-elliott-brennan on 2015-10-14
Thanks for the advice.

This also works when using the printer on a print server.

I'm running Kubuntu 1404 on a desktop. A Brother HL-2140 is attached to a TP-Link TL-PS110U USB print server.

That was pretty easy to set up under Linux (just follow the instructions :))

After assigning an IP address to the server, I added the printer (through CUPS) as:

lpd://**192.168.0.24**/lp1

Obviously you put the IP address you assigned to the machine where the bold IP address is shown.

Then I used the driver you suggested and BINGO! All works well and the machine can be shared with others.

I have another printer (colour laser) CLP-680DW on the same network. If anyone is looking for something that 'just works', I recommend this. Automatically picked up as being on the network, can be used as a Google Cloud Print printer, prints wirelessly, Android phones can print directly to it, as can Blackberrys. Easy peasy to set up for all.

The print server also works as well with Ubuntu/Kubuntu 1204.

Again, thanks for the tip. It helped sort out a problem I had.

---

### Post by luca-dgh on 2015-12-26
Many Many Many Thanks for your work, it has fixed my problem.
Thanks again.

---

