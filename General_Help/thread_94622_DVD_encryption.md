---
title: "DVD encryption"
date: 2005-11-24
forum: General Help
---

### Post by remick182 on 2005-11-24
I've been reading up on DVD's and DVD ROM's since I recently bought a DVD+R(W) drive for my PC and trying to understand how to get the burning process to work.  From reading through other threads here and elsewhere, I've got the skinny on DVD Shrink and DVD Decrypter.  I also have K3B and Gnomebaker.  All seem to work fine (with the exception of DVD Decrypter which won't recognize my DVD+R(W) drive).

Can anyone explain to me the best process for backing up my DVD's on new dics?  I was able to fully backup an entire DVD of Excel Saga with the menus and everything onto a 4.4 GB DVD, and it works flawlessly.  However, I tried to backup just the movie of Polar Express, since it's too big to fit everything on a 4.4 GB DVD, and when I try to watch it, it gives me an error saying that the source is encoded and I that I can't watch it.  Is this because of the new copy protection placed on newer DVD's?  If so, how do I get around it?

---

### Post by sjh on 2005-11-24
[http://www.mrbass.org/linux/ubuntu/dvdshrink/](http://www.mrbass.org/linux/ubuntu/dvdshrink/)

The one I used.  Sorry if you've already read it.

SJH

---

### Post by remick182 on 2005-11-25
Yeah, I've been there already.  Thanks though.  What I really want to know is how to get by the newer encryptions.  I can't play them once I burn them.  This is the error I get:
[I][COLOR="Red"]An error has occured
The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?[/COLOR][/I]

---

### Post by Vlammetje on 2005-11-27
well is libdvdcss installed on your system? If not, please start off by installing it and try to play the dvd again.

---

### Post by Bachstelze on 2005-11-27
While we're at it, can anyone suggest me a good program to rip DVDs to Xvids or whatever codc ? I use dvd::rip but the vids it makes are horrible quality.

---

### Post by remick182 on 2005-11-28
According to Synaptic Package Manager, I have libdvdcss2 installed.  Anything else?

---

### Post by remick182 on 2005-11-29
I'm still having problems with understanding how DVD's work.  The first DVD I successfully copied included all of the menus and extras.  I got playback on my PC as well as my home DVD players.

  The next one was just the movie because I don't have any Dual Layer discs and the movies are too large to fit on the standard 4.7 GB DVD's.  The attempted playback on my PC gives the error:

[COLOR="Red"]An error has occured
The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?[/COLOR]

(And yes I have libdvdcss installed)

  When attempting to play the movie on a home DVD player, I get a blank screen and the player seems to keep cycling or something...like it's trying to find the movie, or some other file.

  I'm trying to find another DVD I might have that is small enough to completely copy like I did with the original.  This is the only way I can think of to continue trouble shooting.

  If anyone has some experience in this matter, it would be greatly appreciated!

---

### Post by Vlammetje on 2005-12-03
Humm... sounds like it needs some file to start the disk in addition to the movie.

BTW I also heard that some DVD burneers can be upgraded to dual layer... might be worth looking into?

Else I have a DL burner for sale ;)

But to get back to your problem: I think you need to find out which of the files initiates the 'play'of the dvd and burn that too.

Fraid I'm fairly new to DVD burning (I have yet to make a succesful copy) so I can't help you with that :(

---

### Post by bionnaki on 2005-12-03
[QUOTE=HymnToLife]While we're at it, can anyone suggest me a good program to rip DVDs to Xvids or whatever codc ? I use dvd::rip but the vids it makes are horrible quality.[/QUOTE]

thoggen

---

### Post by Bandit on 2005-12-03
Try reinstalling libdvdcss again. Sounds like it failed to link up correctly.
Cheers,
Joey

BTW make sure you have at least libdvdcss2-1.2.9 or better. Older versions were laggy..
Cheers..

---

### Post by Drain on 2005-12-04
[QUOTE=HymnToLife]While we're at it, can anyone suggest me a good program to rip DVDs to Xvids or whatever codc ? I use dvd::rip but the vids it makes are horrible quality.[/QUOTE]

Try [AcidRip]("http://untrepid.com/acidrip/")... I believe it's in the repositories. It uses mPlayer and Mencoder, while [dvd::rip]("http://www.exit1.org/dvdrip") uses transcode.  You can probably do some tweaking of the video settings in either one to get better results, though. 

While people are mentioning Dual-layer DVD copying - does anyone have any recommendations about what programs to use to copy a DVD to a Dual-layer disc?

---

### Post by chipmonk010 on 2005-12-04
you guys might be interested in this guide i just wrote:

[http://www.tweakmb.com/docs/dvdcopy.html](http://www.tweakmb.com/docs/dvdcopy.html)

let me know if it helps or if its lacking in anyway

cheers
chris

---

### Post by sjh on 2005-12-05
Some of the newer movies out are a problem for the normal Decrypt-Shrink method.  Though it is normally windows based, I can find information here about the encoding of some movies:

[http://forums.afterdawn.com/](http://forums.afterdawn.com/)

SJH

---

### Post by remick182 on 2005-12-05
I'm in the process of using lxdvdrip.  It seems to work a bit better as far as the whole copy and burn process goes as opposed to using those Windows programs through wine.  I haven't tried _Thoggen_ yet, however, I keep seeing it tossed around in other threads, so maybe I'll try that one too if I continue to have problems.
I know that in one of the threads, the guy mentioned copying the autorun.inf file along with the dvd image file, so that may help as well.  I'll give that a shot on the next movie that gives me trouble.

---

### Post by kingsidy on 2005-12-05
i use xdvdshrink. it works for most dvds. It rip an encod to dvd5. it creates the folders necessary. just burn the folders to a dvd and voila. i burn dvd folders with nerolinux. so far it is the only one that works for me. just google for xdvdshrink.

---

### Post by Robocoastie on 2005-12-05
[QUOTE=remick182]According to Synaptic Package Manager, I have libdvdcss2 installed.  Anything else?[/QUOTE]

Having that package installed is only 1/2 the job. You have to run the script too. See the wiki: [https://wiki.ubuntu.com/RestrictedFormats?highlight=%28Restricted%29](https://wiki.ubuntu.com/RestrictedFormats?highlight=%28Restricted%29)

---

### Post by remick182 on 2005-12-05
[QUOTE=chipmonk010]you guys might be interested in this guide i just wrote:

[http://www.tweakmb.com/docs/dvdcopy.html](http://www.tweakmb.com/docs/dvdcopy.html)

let me know if it helps or if its lacking in anyway

cheers
chris[/QUOTE]

I'm still a little new at this, but it seems like your guide on using [COLOR="RoyalBlue"]dvdrip[/COLOR] is very similar to using [COLOR="SeaGreen"]lxdvdrip[/COLOR].  The apps used seem to be a lot alike, except [COLOR="SeaGreen"]lxdvdrip[/COLOR] does all of those steps for you automatically.  All you have to do is edit the [COLOR="Teal"].conf[/COLOR] file prior to the whole process and it saves you all of that CLI typing.

I will say, though, that it's nice to kinda understand what all of the apps are doing individually.  It helps to see what the entire process consists of.  Thanks.:smile:

---

### Post by remick182 on 2005-12-05
[QUOTE=Robocoastie]Having that package installed is only 1/2 the job. You have to run the script too. See the wiki: [https://wiki.ubuntu.com/RestrictedFormats?highlight=%28Restricted%29](https://wiki.ubuntu.com/RestrictedFormats?highlight=%28Restricted%29)[/QUOTE]
Oh, thanks for that info.  I re-read the original thread and saw that I missed that step. ;)

---

### Post by Tubuntu on 2005-12-22
[QUOTE=remick182]Yeah, I've been there already.  Thanks though.  What I really want to know is how to get by the newer encryptions.  I can't play them once I burn them.  This is the error I get:
[I][COLOR="Red"]An error has occured
The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?[/COLOR][/I][/QUOTE]
 
Change K3b setting, **burn mode** auto to DAO. 

After that you should be able to play them, at least it worked for me..

---

### Post by remick182 on 2005-12-29
I'll try that and see if it works.  Thanks.

---

### Post by babwe on 2005-12-29
the best dvd ripper is Acidrip, it gives u quite a few options to which format u want to rip tp

---

