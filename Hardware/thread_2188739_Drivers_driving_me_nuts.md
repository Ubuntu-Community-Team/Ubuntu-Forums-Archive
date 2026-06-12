---
title: "Drivers driving me nuts"
date: 2013-11-18
forum: Hardware
---

### Post by shaneptd on 2013-11-18
So i am a new linux user. While i have the windows drivers for my motherboard i cannot find any ubuntu drivers. I really need help. 

Motherboard:                                       GA-78LMT-S2P                     (rev. 3.1)                   

- [http://www.gigabyte.us/products/product-page.aspx?pid=3833#sp](http://www.gigabyte.us/products/product-page.aspx?pid=3833#sp) < Official website.

I really don't want to go back to windows having just quit it but this is the only motherboard i have.

---

### Post by heir4c on 2013-11-18
For what do you need drivers? Normally when you install Ubuntu it will work 'out of the box'. 
I have a Gigabyte board tested and I plugged a Laptop HD in with a Ubuntu version installed (from a broken Laptop) and it works directly without installing a driver.
What is it that not work?

---

### Post by shaneptd on 2013-11-18
I have installed Ubuntu 13.0.4, I dont know how to update it and maby that has something to do with it but nothing on board works or is being recognised, installed, updated, or working at all.

I know the motherboard is good i have been using it for over a year without an issue with windows xp.

---

### Post by QIII on 2013-11-18
Hello!

Can you tell us one specific component that is not working?

---

### Post by shaneptd on 2013-11-18
On board realtek sound is my biggest concern and does not work.

---

### Post by heir4c on 2013-11-18
For updating you click on the Dash icon (UbuntuLogo at the top left) and type in the search bar: update
You will see this icon: 

[IMG]http://i.imgur.com/xpCr9z6.png[/IMG] 

Click on it and update first. 


Further: can you give more info about your CPU, graphics card, RAM.
And: more info about the partitions. Open a terminal (The fast way: key combination: Ctrl+Alt+T) and type the following command and press Enter. Post the output here:
```
parted -l
```
(The -l is a little L)

ThanX

---

### Post by shaneptd on 2013-11-18
I apologize i didnt see the relevance since my issue was on board but if it helps i am running a 
Processor: quad core amd fx 4100 
Graphics Card: Geforce 9500 GT
and 4 gigs of ddr3 ram

---

### Post by heir4c on 2013-11-18
To see what driver is used for your graphics card go to the Dash (UbuntuLogo) and search for: Software&Updates Click on the icon to open it.
Than click on the Tab: "Additional drivers" (I think that is it in English, I have a Dutch system) and the system will search for drivers. Post here what he find.
ThanX

(And: don't apologize, we all started somewhere.)

---

### Post by shaneptd on 2013-11-18
The graphics card is working fine. Its the features that came with the board such as Lan and sound. I am even running dual monitor with beutifull resolution.

---

### Post by shaneptd on 2013-11-18
Its doing some massive updating which seems to be taking awhile. I will post back results after it finish's updating. Thank you for the help so far guys and i apologize if i seem like a noob but I am finding myself falling through the proverbial rabbit hole in to wonderland. Everything seems to be far more technical then windows based systems and while i understood a strong learning curve i am none the less finding Ubuntu to be a real treat of an OS. 

I hope these updates fix the issue but i will be certain to post back results as soon as updating is complete

---

### Post by heir4c on 2013-11-18
"I am finding myself falling through the proverbial rabbit hole in to wonderland"
That is a correct and beautiful description of Linux. 

I use Ubuntu now for 5 years and I learned a lot. My knowledge about computers is increased with 500% but I also know now that my knowledge of computers is about 0.005% of what you can know about hard- and software. There is so much to learn, it's a wonderful world. (And when somebody say "I am a Expert, don't believe him :D Nobody can know everything about hard- and software)

Your realtek is a ALC889. There are many issue's with that when I search for it with Google. I hope there is someone who can help you with that.

Greetings
Gerolf

---

### Post by shaneptd on 2013-11-18
Update: I am now fully current in Ubuntu 13.10 and my motherboard still doesnt register with the system nor does sound work yet. I am out of ideas so if anyone can please help i am not to proud to beg,

---

### Post by shaneptd on 2013-11-19
If there is no solution for on board i wonder if it would be possible for me to go pick up a card

---

### Post by heir4c on 2013-11-19
Maybe this link will help. There is a driver for Linux.  (Read first the info on that page!!!)
[http://218.210.127.131/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://218.210.127.131/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)
Accept and click 'Next'. Scroll down and there you find: Linux driver (3.0)

You get the file: LinuxPkg_5.18.tar.bz2 in the downloadfolder.
Go to the Downloadfolder and rightclick on the package and choose to pack it out. 
Than you see the folder: Rt-Linux-HDaudio-5.18
Go inside and click on "Install" That will install the driver.

I hope it will work.

---

### Post by shaneptd on 2013-11-19
I click it and it opens a txt editor

---

### Post by The Spectre on 2013-11-19
Check your Sound Settings and confirm it is using the correct one.

It may have defaulted to HDMI or Digital out. (See Screenshot Below)

[ATTACH=CONFIG]247929[/ATTACH]

---

### Post by heir4c on 2013-11-19
> 

    I click it and it opens a txt editor 



Yes, that is a "bug" in Nautilus. It's not really a bug but the default settings in nautilus have changed. Why they did that, I don't now but here is the solution:
Open nautilus and make the window to take the hole screen.
(I mean to use this (the square)):
[IMG]http://i.imgur.com/9P4PlMw.png[/IMG]

Than move over the top of the screen and you see normally one word: Files (I think that's what there is in English, I have a Dutch version, so sorry about that.)
Click on it and choose: preferences
Than go to the Tab: behavior (or something like that)
Look to the mousepoint in my screenshot to what you must check 
You must choose: Ask every time.

[IMG]http://i.imgur.com/fG0OmX4.png[/IMG]

When you now click on that Install file you get a window like this:
(Click on the button: Executing in Terminal)

[IMG]http://i.imgur.com/lrW6J3E.png[/IMG]

---

### Post by shaneptd on 2013-11-19
Well i got this out of the terminal 

shane@shane:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
---------------------------------------------------

In the Sound Settings it is showing only anologe and still no sound and not to be snarky but i already checked to make sure nothing was muted lol. Also i do not have a mode setting above test in my sound setting menu. I do not know if that is important.

---

### Post by shaneptd on 2013-11-19
I apologize for my simple explanations . I honestly don't know enough about the os to properly self analyze the issue but i did ensure mute was off. I also tested a different pair of speakers and 2 pairs of head phones just to make sure but i was watching youtube fine just prior to installing Ubuntu so i am relatively certain it is something in the OS. My luck it is my fault somehow.

---

### Post by shaneptd on 2013-11-19
So i installed pulse and it did nothing either

---

### Post by shaneptd on 2013-11-19
I bought a USB sound card and it worked right after plugging it in. I suppose i am going to have to use it. This motherboard is very hostile to ubuntu. None of the on board works and there is no support or help for people with it so for future reference i will not be purchasing from gigabyte anymore.

I took this action because i am done with microsoft and never using there products again. I guess i am going to have to buy a new motherboard when i get the money to afford one. Thank you every one that tried to help me but an OS without sound is worthless to me so i had no choice but to throw money at the problem.

---

### Post by The Spectre on 2013-11-19
A lot of computer hardware is supported directly by the Linux Kernel.

Maybe support for the Realtek ALC889 was improved in a later Linux Kernel release.

It might be worth while to Download the Ubuntu 13.10 ISO and boot into a live session to see if the sound works.

If it works then you might want to move to Ubuntu 13.10.

Which might not be a bad idea anyways since Ubuntu 13.04 reaches it's end of life in January 2014 and will no longer be supported.

---

### Post by coffeecat on 2013-11-20
You say things like:

> **shaneptd said:**
> nothing on board works

and

> **shaneptd said:**
> This motherboard is very hostile to ubuntu. None of the on board works and there is no support or help for people with it so for future reference i will not be purchasing from gigabyte anymore.

Yet your problem appears to be confined to the onboard soundcard. A few thoughts for you. The motherboard is not hostile to Ubuntu - one particular chip appears to have a substandard Linux driver, and which is not only found on Gigabyte hardware. If you don't purchase from Gigabyte again, that is your decision, but I have to say that I have a Gigabyte board where everything just works in Ubuntu. You must also bear in mind that if you buy a motherboard from another manufacturer, you might be unlucky enough to buy one with a component that is not well supported.

As far as help for that soundcard is concerned, a little googling found this:

[http://askubuntu.com/questions/151472/no-sound-after-updating-from-11-10-to-12-04](http://askubuntu.com/questions/151472/no-sound-after-updating-from-11-10-to-12-04) 

That workaround may or may not work with 13.04, but it might be worth a try. If you need help with it, post back and someone will be able to tell you how to get that options line into the alsa-base.conf file.

---

### Post by shaneptd on 2013-11-20
Spectre i already stated i fully updated ubuntu. 

Coffee if you read that whole post it states that it is still not solved.  I am tired of saying this. NOTHING ON BOARD WORKS. NO lan No sound No on board video NOTHING ON THE BOARD WORKS> last time i am saying that and responding to a comment based on that,.

---

### Post by coffeecat on 2013-11-20
> **shaneptd said:**
> I am tired of saying this. NOTHING ON BOARD WORKS. NO lan No sound No on board video NOTHING ON THE BOARD WORKS>

Please stop exaggerating. If nothing on board worked, you wouldn't be able to use the USB sound card you added and you certainly wouldn't be able to to boot up.

As far as specifics are concerned, the [specifications for your motherboard]("http://www.gigabyte.us/products/product-page.aspx?pid=3833#sp") say that you have the Realtek 8111E chip for LAN. I can tell you that I have that same LAN chip in no fewer than **two** different motherboards and the LAN just works in each one with Ubuntu without any configuration on my part. If you can't make a connection between your Ubuntu system and your router from that motherboard, you need to look for the problem elsewhere and give more details. Just shouting in capital letters won't get you the help you need.

---

### Post by The Spectre on 2013-11-20
> **shaneptd said:**
> Spectre i already stated i fully updated ubuntu. 

Coffee if you read that whole post it states that it is still not solved.  I am tired of saying this. NOTHING ON BOARD WORKS. NO lan No sound No on board video NOTHING ON THE BOARD WORKS> last time i am saying that and responding to a comment based on that,.
Saying "nothing on the board works" was not very helpful in pinpointing what problems you are having. It's like going to the Doctor and just saying i'm sick, the Doctor would also need more info in order help.:D

You stated that you are running Ubuntu 13.04 which uses Linux Kernel 3.8.8, Ubuntu 13.10 uses Linux Kernel 3.11 and like I was saying m[COLOR=#000000]aybe support for the Realtek ALC889 [/COLOR][COLOR=#000000] as well as some of the other hardware [/COLOR][COLOR=#000000]was added or improved in a later Linux Kernel release.[/COLOR]
[http://kernelnewbies.org/Linux_3.11-DriversArch](http://kernelnewbies.org/Linux_3.11-DriversArch)

You can confirm what kernel you are using by typing this into terminal...
```
uname -a
```

And just to rule out the possibility, check your BIOS setting and make sure that none of them are disabled.

Some motherboards will automatically disable on board Video when a dedicated Video Card is added.

---

