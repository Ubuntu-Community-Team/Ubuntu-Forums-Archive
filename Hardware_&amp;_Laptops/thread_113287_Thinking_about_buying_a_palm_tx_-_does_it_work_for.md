---
title: "Thinking about buying a palm tx - does it work for you?"
date: 2006-01-06
forum: Hardware &amp; Laptops
---

### Post by André on 2006-01-06
Hi everybody,

i am thinking about buying a palm tx which costs about 300&#172;. So i just wanted to know. Does it work well with Ubuntu or Kubuntu?

I would like to sync my addresses and appointments with kontact/evolution.

Or would you suggest some other device for that purpose?

Thanks for any answers
Andr&#180;e

---

### Post by MartinG on 2006-01-06
Dunno about tx, but I've got a Treo 600 which syncs beautifully with Kontact

---

### Post by lorenco on 2006-01-06
I have a Treo 650 Works like a dream.  Kpilot- Kontact & KDE PIM..

Should be OK if it runs Palm OS 5 ... or even 4.

Cheers.

---

### Post by André on 2006-01-06
One things that really attracts me to the tx is that it has a bluetooth and wlan module included. 

The Treo 650 is a smartphone, isn´ t it?

Greetings
Andr´e

---

### Post by André on 2006-01-06
Does no one actually owe a Palm TX and tell me if he is satisfied with it?

Greetings
Andr´e

---

### Post by André on 2006-01-07
Hi,

me again ;-)

Has anyone of you tried syncing a lifedrive with ubuntu?

Greetings
Andr´e

---

### Post by jainauk on 2006-01-07
I have the tx and I love it so I can definately recommend that.  As for syncing I have managed to get limited syncing with the tx and jpilot (only the adress book etc, no extra files).  It seems like others have got the rest to work so it is just a matter of figuring it out. Basically just installed jpilot and pilot-link.  DO NOT follow the ubuntu guide for setting up a palm it just screws things up.  Tx works out of the box on Breezy. Hope this helps!!

---

### Post by André on 2006-01-07
Hi jainauk,

thanks for your post. Here come a few questions about it:

Did you try to sync with evolution? How did this work?

What excactly do you mean by it works out of the box? Sounds like it does not sync so it does not work right?

Or did i get something wrong?

Thanks again for your reply. Good to hear that you like it.

Greetings
Andre

---

### Post by jainauk on 2006-01-08
I did try to sync with evolution but have only managed to get it to work once and cannot seem to replicate whatever I did the first time.

As for it working out of the box I meant that as long as you have pilot-link installed with jpilot it works on the first try.  I can get it to sync up the calendar, address book, to do and memo but when I try to do a back up of my programs it doesn't work.  I think I have narrowed it down to a problem with pilot-link application.  This problem seems to be fixed in the new version but it is not ready for Breezy yet so I have yet to try it out.  

Hope this answers your questions (as you have probably figured out I am a newbie to ubuntu so I am sure that I will generate many more questions than answers ;-) ).

Jainauk

---

### Post by André on 2006-01-08
Hi Jainuak,

thanks for your reply again. I think i have to look for another PDA. Evolution syncing is really important to me because i do all my address and appointment stuff in it.

Do not care about the newbieness. I use Ubuntu now for a year and i have so many questions experiencing something new everyday... so somehow we are all newbies ;-)

Greetings and thanks again
André

---

### Post by Brigrat on 2006-01-08
I am still new to ubuntu, and have a Kyocera 7135 Smartphone.  I synced right up with evolution and I used jpilot.  Granted it is a dinosaur, but so am I in some respects.  I only had one burb in the syncing and back up so the info from earlier about a newer version is good news.  from what I have read jpilot seems to be the one of the better link programs and it tied right in with evolution.  I hope that this supports your questions and the other replies.

---

### Post by André on 2006-01-09
Hi,

will i be able to use jpilot in evolution?

How does it integrate? Special sub menu? Button?

I am also very new to it and do not have any syncing item to try out right now.

Greetings
André

---

### Post by Brigrat on 2006-01-09
jpilot installed and ran up with now issues, had to tweek the cinfig just a little as i am using the serial port vice the usb, but it just works.

---

### Post by André on 2006-01-09
Hi Brigrat,

thanks for your post again.

I think my question was a bit irretating so here comes another one ;-)

Can you use Evolution to arrange your contacts and appointments and then sync them via jpilot? Or is there even a plugin for evolution?

Greetings
André

---

### Post by jonsson on 2006-01-20
I have just replaced my worn out Tungsten T with a brand new Palm TX (love the Wi-Fi!) and I have been unable to sync it with Jpilot. I have been syncing the TT with Jpilot for years with no problems whatsoever but with the TX all I get is:

dlp_ReadSysInfo error
Exiting with status SYNC_ERROR_PI_CONNECT
Finished

(I managed to sync the adress book with Evolution but gpilotd crashed when syncing the calendar. Anyway, I'd prefer Jpilot as it is small, simple and has always worked.)

Oh, while writing this I found this [http://www.jpilot.org/pipermail/jpilot/2005-June/005158.html](http://www.jpilot.org/pipermail/jpilot/2005-June/005158.html) but I keep getting connection refused from the server so I cannot see any replies! :-/

---

### Post by André on 2006-01-21
Hi jonsson,

so the tx does not look like my best choice?? :-(

I really liked its stats but if i will not sync i guess it is not for me :-(

Maybe i try the Tungsten E2 with a wlan adapter. What do you think?

Greetings
André

---

### Post by jonsson on 2006-01-21
I think the TX seems to be better in terms of value for money (wifi, larger screen etc). I would also guess that they are similar enough to present the same problems.

I'm still hoping to be able to get it to work with J-Pilot. Apparently, jainauk above has it syncing with J-Pilot.

Maybe I should experiment with Multisync? I haven't tried that yet.

---

### Post by 18nikko on 2006-01-21
Hi,
I got my T|X on Thursday and my experience so far has been mixed. I tried gpilot and didn't have much luck. Then I tried jpilot and had the same problems as Jonsson. So, I tried the most recent versions of pilot-link and jpilot which I compiled from source and installed in /usr/local. I have /usr/local/bin first in my path so this works. Now I can sync and backup using Jpilot, but all the plugins aren't there, I probably need to compile and install each seperately. Also I cant install software using jpilot, the dialog comes up and the link dies. I can insall from the command line  using: pilot-xfer -p /dev/pilot -i <program name> and that works without hitches so the problem is in jpilot, I guess I should cross post on the jpilot list.

I have however discovered some neat applications on [http://www.freewarepalm.com/](http://www.freewarepalm.com/)

PalmPDF is a port of xpdf for palm and works much better than the adobe
viewer which hasn't been updated in aeons. I tried reading a genetics paper
and some math papers and it worked pretty well though the font kerning gets blocky at higher magnification.

There is also a dvi viewer, which is good for latex documentation.

The wireless works great, and the big screen is nice, especially landscape mode. I just wish palm played better with linux. I have great interest in keeping this thread going as I would like to get the best of my palm. Lets hear other peoples experiences.

Cheers
Nicholas

---

### Post by jonsson on 2006-01-21
Aargh, guess I'll have to try compiling newer versions as well then. 

I have also just found PalmPDF and was eager to try it out but syncing has priority. ;-)

---

### Post by jonsson on 2006-01-23
It works! :) 

I'm not quite sure what I did but suddenly it just works! As long as I hit the hot sync button on the Palm before I hit the sync button in J-Pilot, it just works! :) 

It syncs the calender, contacts etc and I can install prc/pdb files to the Palm. :D :D :D :D

---

### Post by 18nikko on 2006-01-24
Hi,
I am able to sync with jpilot, and pilot-xfer works for installing software. I would like to get things smoother though.

Nicholas

---

### Post by André on 2006-01-25
Hi guys,

sounds like good news for me. I am pretty new to the pilot stuff: Is jpilot able to sync the PDA with Evolution or do i have to keep a seperate adressbook in jpilot?

I am just asking because i like my evolution adressbook for snycing with my Sony Ericsson T610 and including Gaim contacts. This way i keep everything together :-)

Greetings
André

---

### Post by jonsson on 2006-01-25
J-Pilot is a separate program. It's a Palm Desktop clone that does basic PIM and syncs with Palm OS PDAs. I don't think it can sync with Evolution for you.

I won't promise anytning but previous Palms have, as far as I know, synced well with Evolution and my experience with J-Pilot suggests that this one works pretty much like the previous ones.

Oh, and once you get used to having a PDA, it will become your *main* calendar, address book etc. I input nearly all new appointments etc on the Palm. Syncing is done mainly to have a backup.

---

### Post by André on 2006-01-25
Hi,

what do you guys think about the Nokia 770?

You could use this software for PIM: [http://oss.kernelconcepts.de/gpe/](http://oss.kernelconcepts.de/gpe/)

They say it has reached a stable level now. So what do you think about it?

Greetings
André

---

### Post by linuxden on 2006-02-23
Hey,

Any news on how the T|X works with Ubuntu? Its one of my main choices, but obviosuly synching is essential...

Thanks for an Update form T|X users...

---

### Post by jonsson on 2006-02-23
I've had my TX for almost a month now and once I got it working (see above) it syncs fine with Jpilot. I have not bothered to try anything else after that since I've been happily using Jpilot for years anyway.

Btw, I have now returned my TX to the shop for a repair/replacement since there was a constant hum/buzz in the audio output. 

For the long time Palm users I must also stress the fact that the TX (like all new Palm units) come with *Graffiti2* (due to a Xerox patent). IMHO, Graffiti2 sucks. :evil:

---

### Post by cucisan on 2006-06-03
hi,

as of ubuntu 6.06 syncing my PalmTX with Evolution worked out of the box:
just used /dev/pilot and changed type to USB, enabled address-, todo-, calendar- and memosync, pressed the hotsync button on my cradle tadaa sync'd ;)

hope that will make your decision easier for getting yourself a PalmTX.

---

### Post by bouncingmolar on 2007-10-13
sorry to dig this old post up again, but in your opinion is jpilot better for syncing with a palm than the gnome-pilot?   especially with evolution

---

### Post by ShamusPatt on 2007-10-20
> **bouncingmolar said:**
> sorry to dig this old post up again, but in your opinion is jpilot better for syncing with a palm than the gnome-pilot?   especially with evolution

JPilot has its own "desktop" application, much like the Palm Desktop on Windows. I don't believe it can communicate with Evolution - you need gnome-pilot to do that.

I haven't done much more than dabble with JPilot so I can't comment on which is better. I chose gnome-pilot because I was tired of maintaining my contacts in two places.

I've found syncing hit-and-miss, though. I had it working fairly reliably with libusb on Feisty. It seems completely bust under Gutsy. The network sync works better, but it seems to stall on me fairly consistently (on Feisty and Gutsy).

I'm still trying to get sync working again (I don't really want to go back to Feisty). I'll post something if I get a solution.

---

### Post by erunamo1221 on 2007-10-24
I have had a Palm T|X for about a year and I found that syncing my calendar, contacts and tasks with Evolution (gnome-pilot) works great with Ubuntu (both Feisty and Gutsy - just upgraded).  I was very impressed with ubuntu's syncing versus Palm Desktop (I could never get it to sync right with Outlook a).  

The only issue I have is that every time I sync with Evolution, I have to go to Edit>>Synchronization Options in Evolution.  I haven't figured out why, but before I go to sync options, I can push the HotSync button all I want, but the palm won't sync.  I haven't needed to change anything in Sync Options, as long as I open the window, then close it, it seems to recognize (or look for) the Palm.

Recently, I have been trying to find a way to sync files to my Palm (I like to use it as an mp3 player).  In gnome-pilot, there is an option to enable file uploading, and I've enabled it, but I can't figure out how to upload files yet...does anyone have an idea how to do this?

As far as a recommendation on the Palm T|X, I highly recommend it for all of its features (wifi, bluetooth, , but I've consistently found that there are compatibility issues for a lot of freeware and accessories.  It seems like many people don't consider it because of its similarity to the Tungsten T5.

---

### Post by bennettboggess on 2008-01-19
I have had my TX for about a month now, and can sync with jpilot and evolution. I have been able to install files and programs with jpilot, but it does not give the option to install to a card instead of main memory.

---

### Post by jonsson on 2008-01-20
I've now also managed to sync a TX and a T3 with Kontact without major issues. It's not as good as Jpilot, but then again Kontact is nicer on the desktop side.

---

