---
title: "Ubuntu works on Acer Aspire 5571 AWXMI"
date: 2007-01-07
forum: Hardware &amp; Laptops
---

### Post by ekka on 2007-01-07
Hi all

Just managed to install the Ubuntu Linux (6.10 Edgy Eft) on my Acer laptop (Aspire 5571 AWXMI, similar to 5570). I had to do some tweaking but its working perfectly fine now. I would say this is my only fully functional working Linux which I ever installed. And I am impressed; it’s as good as Windows and better still it’s completely free!

I first tried to install a Linux way back in year 2000 and it was a complete failure. I then tried with Red Hat (I think it was 7.1 or something like that) the installation was fine but I couldn’t figure out what I should do after that! Since there I couldn’t connect to internet then nor there are was any good software for day-to-day use like Open Office.

After my bad experience with Linux I thought I would never even look at it again. But since I’ve been hearing lot about Ubuntu these days, thought would give it a try. Looks like its going to stay here for long time.

**Hardware that were detected on install:**
Wi-fi card, Network card, Modem, CD/DVD drive, detects flash drive just like windows.
Sound card was detected on install but I have to manually tweak the alsamixer.
Screen resolution was changed from default 1024X768 to 1280X800.

**Hardware that are yet to be tested:**
Orbicam, 5-in-one card reader, Bluetooth

Happy Computing!

---

### Post by babooka on 2007-03-05
Did you get wifi card to work?

I've just tried Ubuntu 6.06 on my aspire 5570, and I was unable to get it to work.

---

### Post by abuadam on 2007-03-10
hi
mine is 5570
but wifi not detected, modem not detected

quite frustating

btw, did you use pc or alternate version?

---

### Post by ekka on 2007-03-12
My wi-fi didn’t work OTB, had to do little bit of tweaking (doesn’t exactly remember what I did though)
See if your wi-fi card is detected

```
sudo lshw -C network
```

You should see your wi-fi and network card in the list.

Also, install Gnome Network Manager.

---

### Post by arkuen on 2007-04-19
Ok ive got the Acer 5570 and Wireless worked right OTB. I cannot however figure out how to get the display past 1024x768 it looks horrible and my sound card says its working but there is no actual sound? 

Can you describe how you got your video and sound working?

---

### Post by truth_forum on 2007-05-05
hi:

i just secured acer Aspire 5570 with free linpus, although havent installed any OS yet. im planning to install  tri-boot, got xp (got it for free from one who gave me the unused installer); linpus ( maybe no hardware issues because it comes with the unit and with acer support) and ubuntu 6.10 edgy.  im monitoring this thread for any possible hardware issues with edgy especially the wi-fi and the resolutions. i would really like to run ubuntu on this laptap.  

is the 5570 hardware the same as 5571? 

by the way; i recently received from Ship It 6.06 lts dapper drake disks, its very cool with free (4) ubuntu stickers. already stuck one in my laptap and hopefully will be running on ubuntu and using wireless network to surf the net. 


thanks...

---

### Post by truth_forum on 2007-05-12
i have already installed edgy on my 5570. 

wifi detected.. although havent tried it yet... 



how can i get the gnome network manager? is it in the package manager? 
however no sounds...

any advise???

thanks ..

---

### Post by ekka on 2007-05-14
I advice you to use the Feisty Fawn as it has Gnome Network Manager pre installed and also takes care of your resolution with 915resolution. Everything worked OTB for me with Feisty, except for sound which I enabled after fiddling with alsamixer.

For Edgy you can always install both Gnome Network Manager and 915resolution from Synaptic Package Manager.

For sound try

```
alsamixer
```

and see if the speakers are enabled.

---

### Post by isagani on 2007-05-14
I'm planning on buying this laptop. Could any of you who already own one tell me if the external VGA out in this system works. If not, how can it be made to work? Thank you so much.

---

### Post by EduMaxwell on 2007-05-15
Fiddling with ALSA might just do the trick.  It did on my Acer Aspire 5051.  

If you want to try it:
1. Open ALSA mixer (double-click on the speaker or open it with the menu).  
2. Go to Edit > Preferences.  
3. You will have options to enable various speakers, inputs, outputs.  "Surround" might be what you are looking for.  If not, use trial and error by enabling and testing.
4. *Make sure nothing is MUTED* in ALSA

Did it work for you?

---

### Post by brian.freelancer on 2007-06-01
I almost dropped Ubuntu because I could not get sound on my Aspire 5570. The answer is so dumb, though..LOL. 

Double click on the speaker icon and make sure you have the "surround" slider maxed out. Just to be safe, check at the bottom of the "surround" slider and see if you haven't got it muted. That should work.

Remember this when you want to listen through headphones because Ubuntu does not automatically mute the laptop speakers so you'll have to mute the "surround". This won't affect the headset.

By the way, anyone tried using their bluetooth? mine does not work. 

Also, how about the modem? I tried to dial-up but "modem was not detected"

---

### Post by tonti on 2007-06-03
bluetooth is working for me... at least it can receive files.. haven't tried sending though.. will wrestle with making the modem work late :p

anyway, anybody having problems with the video playback? it seems a little too bright compared to windows media player? is it because of the crystalbrite technology?

also, is it possible to enable te\he 'tap & drag' on the touchpad?

---

### Post by Siad on 2007-07-01
Hello..I'm kinda new here...well anyway i recently got an Aspire 5570 laptop. The problem iz tat i dunno how 2 activate Bluetooth on my laptop. I try pressing the Bluetooth button but a message 'No Device' shows up on the screen. Why is it? Is not a Bluetooth adaptor found built-in within the laptop? Please I need an urgent reply.

---

### Post by dwaldie on 2007-07-03
do you have the 5570z?  I do and it has no bluetooth, just the switch to activate it.  

Dave

---

