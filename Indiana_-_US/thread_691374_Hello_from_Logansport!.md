---
title: "Hello from Logansport!"
date: 2008-02-08
forum: Indiana - US
---

### Post by aeklabunde on 2008-02-08
This is my first time on the IN LoCo forum, and simply wanted to say "hi" and see if there are others from the Logansport area.  I've been an Ubuntu user for 3 months and it is now my primary office machine for web design.  I keep XP on a separate partition, and on my wife's machine, for building IE compatible stylesheets, otherwise I'd be 100% Ubuntu!  I think the best thing Ubuntu has going for it is the intuitive GUI and the fantastic open source/free software available.  I think the biggest hindrance to Ubuntu growth among the general public is the necessity of using CLI for performing certain administrative tasks, --and the forum advice that often recommends Newbies to blindly use the CLI when solutions can be attained through the GUI.  

Those are my thoughts that may stimulate a little discussion!

---

### Post by simon.a.ruiz on 2008-02-13
Hello, aeklandunde, and welcome aboard!

Re: the biggest hindrance. I submit that probably the vast majority of what REQUIRES a CLI to get done on Ubuntu is low level enough that most people on other OSs wouldn't be doing it unless they were technically-inclined enough to be able to brave the console waters anyhow. Things like mounting remote filesystems locally, setting up special services, flipping esoteric switches, etc. Things that non-technical people would think of doing generally have a GUI anymore.

While a broad generalization, I think it's mostly accurate, and I think it's becoming more accurate with every Ubuntu release.

What do you think of that idea?

I completely agree that advice to newbies should definitely steer clear of the CLI unless absolutely necessary.

On the other hand, unless explicitly stated, how can we judge who's a newbie and who isn't?

As a professional technology person, if someone asks a question that implies they have the slightest idea what they're doing (because they seem to speak the lingo, or because it's an esoteric request) I'd much rather say "Here's a command/configuration file you should look at" than go through the imprecise, tedious mechanics of explaining where in the GUI they should be looking.

I'd certainly be open to re-evaluating my advice if the questioner happens to not be comfortable with my first suggestion and says so, but I don't automatically assume everyone is afraid of the command line.

The command-line, while a "Scary Thing" to the uninitiated, can be significantly easier, simpler and faster than any GUI, so people on the other side of the learning curve naturally tend to avoid clunky GUIs in favor of simple, precise commands wherever they're familiar with them.

I think this is probably a big reason why CLI advice may be given out inappropriately at times. I don't suggest it's excusable or good, just that I can understand the tendency.

Thoughts?

:-)

---

### Post by aeklabunde on 2008-02-14
Thanks for the well spoken response, Simon!

I think that the majority of professionals (non-technical) who use computers every day, would be considered Newbies to any OS other than the one they currently use.  But these same people are often very proficient at getting around, and even taking administrative actions, by navigating the GUI, as slow and sloppy as it may be.  I think the reason we gravitate toward the GUI, and prefer it, is that it leaves visual "breadcrumbs" of how we got to where we are. And it enables us to fix what we mess up without needing to learn another language.  Our lives don't revolve around the PC, we just want it to do what we need it to, and sometimes we ask a lot.

I've won two new recruits to Ubuntu and lost a third.  And I am forcing conversion on a fourth!  - I just ordered for her an Everex with the "green" VIA processor and with gOS preinstalled (she couldn't argue with $199 for a new desktop).  I believe that the gOS is a flavor of Ubuntu.  She is still using Windows 98, and the last person I helped leap from 98 to Vista is still very lost (but I don't have time for Vista, literally, so I might not have been the best teacher!).  If anybody has experience/opinions on the gOS or the VIA C7-D processor, I'd love to hear it.  (oops, should start a new thread for that?)

Thanks!

---

### Post by simon.a.ruiz on 2008-02-15
Re: Newbies to any OS other than the one they currently use. That's true, and it's certainly a "barrier to entry".

Certainly, command-line stuff implies learning "another language", I agree. I also agree that it's an investment in time, effort, and patience that that majority of people shouldn't need to make.

They still have to spend the time, effort and patience to learn the language of windows, icons, menus, and pointers. They look at all the icons and menus, and that GUI decides what they can do and how they can do it. If they're curious, they can indeed learn more about that GUI, but in the end it still dictates what they can and can't do.

The CLI steps outside of those supports/boundaries. It's a scary place when you're used to GUIs, being able to do anything but having to know how to ask for it, I can understand that could be scary. (Though I started with CP/M on a green and black screen Epson QX-10, and my dad taught me my way around GWBASIC when I was in early elementary school, so I can't REALLY understand fear of the command-line, as I've never experienced it. Sure, my first time being faced with a UNIX command shell I had no idea how to do anything, but I just looked for information to figure it out.)

At some level, though, I think that if you ask a lot from your computer, especially if you're asking unusual things from it, that it's worth spending the time to learn how to tell it exactly what you need from it.

I mean, you can't just tell a saw that you want that pile of wood over there to become a table, can you? You need to invest the time, effort and patience to learn how to use that saw to get what you want out of the wood, and the more time, effort and patience you put in the closer that table will look to the one you had in your mind to make, the higher quality it will be, and the less time it'll take you to make it.

I'm curious, though, what sorts of things would a non-technical person want their PC to do that Ubuntu can't do through a GUI?

Re:gOS. It's Ubuntu with the Enlightenment Desktop Environment and a green theme. Neat, light-weight, blingy desktop environment that's been a long time in the making.

What's a VIA C7-D processor? (And yeah, it's probably worth its own thread, so people who may be able to shine some light on it have a chance to see your question.)

---

### Post by aeklabunde on 2008-02-17
Re: I'm curious, though, what sorts of things would a non-technical person want their PC to do that Ubuntu can't do through a GUI?

When I first set up Ubuntu, here's the list of things that Forum Members gave commands for and for which the GUI seemed to lack (Now I know that some of these things can be accomplished via Nautilus, though even that  requires a command to launch)...

-Resetting permissions on multiple partitions that only had root permissions when created. Being new to linux, I couldn't figure out why I couldn't use the extra partitions I had made with Gparted! Fortunately, I at least knew what "permissions" are from using linux-based web hosts.

-Moving my home directory to another partition for easier reinstallations of Ubuntu. (Got scared --seemed like more work than what it was worth.)

-Ubuntu would alternate between the on-board sound and the sound card on each boot-up, even though I set the sound card as the default in Preferences>Settings>Sound. (A GUI problem?) A command fixed that (though the keyboard volume control usability still alternates!)

-I still don't have splash screen because that requires some command to fix.  

-Installing the appropriate libraries for various common (proprietary) media formats. I have since discovered that these are now available in Applications>Add/Remove_Applications>Application>Ubuntu_Restricted_Extras.  And the command line approach was a lot more work --and just to be able to rip MP3's!  That's as basic as computer use gets these days!

Well, those are some of the issues I remember dealing with via CLI.  And I'm sure that many of those had, or now have, a GUI solution.  And some just require bug fixes within Ubuntu (e.g. splash screen and sound card).

The beauty of the GUI is that "learning" it's "language" is an intuative process, it requires no teacher, no instructions, no map. A good GUI is it's own map. You can see the road ahead and behind.  Hence my "breadcrumbs" analogy. It can be learned by simply doing it.  CLI is truly a language.  There is no intuition that can prompt me to type in "sudo apt-get install liblame0" or "sudo apt-get install gstreamer-plugin-bad" without first memorizing what each element means and does.

And, yes, there are saws that build tables! Take a tour of Cole Hardwoods/Indiana Dimensions, Inc. if you want to see such equipment in action. It still requires user input, but it is all done via wonderful GUI's.  And it is streamlined to be more efficient then a human could dream.  And the human input still allows for creativity and various levels of quality.  And, there's always a hand saw laying around somewhere, for those few times when manual "hacking" is required!

The OS that wins is the OS that can automate as many processes as possible via its GUI and do so as efficiently, or more efficiently, than command line. I believe that is the mission and purpose of "Ubuntu Just Works."  And that is why I am on board! 

This has been a fun discussion, and  I look forwad to becoming more comfortable with command line in the coming months. And I know to come to you when I've got questions, ..so Thank You! I'm sold on Ubuntu, and look forward to each new release!

Thanks for the insight about gOS!  I should be setting up the system in the next few days, and I'm looking forward to it!  Also, I'll post a new thread about the VIA CPU when I get a chance.  Right now, it's dinner time!

---

### Post by thecure on 2008-04-20
> **aeklabunde said:**
> This is my first time on the IN LoCo forum, and simply wanted to say "hi" and see if there are others from the Logansport area.  !

I grew up in Logansport. My brother and sister-in-law still liver there... the old trout farm on HW35.

As far as your other comments go, can you remember the first time you used Windows of any variety? If you've only used Uuntu for three months, give it a little more time and you'll see how a lot of things make much more sense.

---

### Post by aeklabunde on 2008-04-27
It's been two months since my first post in this thread, and I still love Ubuntu and have won a couple more converts!  I just installed Hardy 64 bit on a Compaq Presario F756 laptop and everything "just works" great.  I still shy from command line, though I use it from time to time with ffmpeg. A command from Cappy[http://ubuntuforums.org/showthread.php?t=432295]("http://ubuntuforums.org/showthread.php?t=432295") just provided me with a very fast fix to install Skype which otherwise won't work with AMD64. Now it works great!

You escaped Logansport! I've been here almost ten years now and now that I am happily married and have three kids, the area is growing on me! I live past France Park in a forested neighborhood (Ridgeview) above the Wabash.

I didn't realize there had been a trout farm on 35! I'm interested in learning more about the history of that and will have to Google it!

---

### Post by simon.a.ruiz on 2008-04-28
> **aeklabunde said:**
> When I first set up Ubuntu, here's the list of things that Forum Members gave commands for and for which the GUI seemed to lack (Now I know that some of these things can be accomplished via Nautilus, though even that  requires a command to launch)...

Sorry I missed this when you first posted it!

> **aeklabunde said:**
> -Resetting permissions on multiple partitions that only had root permissions when created. Being new to linux, I couldn't figure out why I couldn't use the extra partitions I had made with Gparted! Fortunately, I at least knew what "permissions" are from using linux-based web hosts.

-Moving my home directory to another partition for easier reinstallations of Ubuntu. (Got scared --seemed like more work than what it was worth.)

I'm not sure what you mean about partition permissions.

Yeah, partitioning stuff is still kind of a pain, though GParted is a beautiful GUI for partitioning.

That doesn't keep you from having to understand what you're doing to use it.

> **aeklabunde said:**
> -Ubuntu would alternate between the on-board sound and the sound card on each boot-up, even though I set the sound card as the default in Preferences>Settings>Sound. (A GUI problem?) A command fixed that (though the keyboard volume control usability still alternates!)

-I still don't have splash screen because that requires some command to fix.

Hardware bugs will be with us for the rest of time. :-)

Fortunately, as Linux gains mindshare hardware manufacturers will start having to make sure their hardware works under Linux if they want to reach their entire market.

> **aeklabunde said:**
> -Installing the appropriate libraries for various common (proprietary) media formats. I have since discovered that these are now available in Applications>Add/Remove_Applications>Application>Ubuntu_Restricted_Extras.  And the command line approach was a lot more work --and just to be able to rip MP3's!  That's as basic as computer use gets these days!

Yeah, an unfortunate primary effect of current patent law, if I recall correctly. At least you didn't have to try to move you're iTunes Music Store collection over. ;-)

> **aeklabunde said:**
> The beauty of the GUI is that "learning" it's "language" is an intuative process, it requires no teacher, no instructions, no map. A good GUI is it's own map. You can see the road ahead and behind.  Hence my "breadcrumbs" analogy. It can be learned by simply doing it.  CLI is truly a language.  There is no intuition that can prompt me to type in "sudo apt-get install liblame0" or "sudo apt-get install gstreamer-plugin-bad" without first memorizing what each element means and does.

Be careful! Sometimes a slick GUI lets you take off running before you learn the fundamentals of walking and looking where you're going. ;-)

Yeah, there's definitely some benefit to the fact that a GUI is visual and the most important options/commands are right in front of your face as opposed to buried in a manpage somewhere.

On the other hand, you really should read up on your GUI programs; you may find out it's got a lot more functionality than you can tell by looking at it.

> **aeklabunde said:**
> And, yes, there are saws that build tables! Take a tour of Cole Hardwoods/Indiana Dimensions, Inc. if you want to see such equipment in action. It still requires user input, but it is all done via wonderful GUI's.  And it is streamlined to be more efficient then a human could dream.  And the human input still allows for creativity and various levels of quality.

I stand corrected. :-D

I'll guess, however, that you still have to have a pretty good grasp of carpentry and how all the automated parts work in order to use it well. Am I right?

> **aeklabunde said:**
> And, there's always a hand saw laying around somewhere, for those few times when manual "hacking" is required!

*lol* Of course!

IMHO, REGARDLESS of how great your GUI is, there will ALWAYS be a place for hand hacking.

> **aeklabunde said:**
> The OS that wins is the OS that can automate as many processes as possible via its GUI and do so as efficiently, or more efficiently, than command line. I believe that is the mission and purpose of "Ubuntu Just Works."  And that is why I am on board!

The OS that wins? :-D

Especially in Linux, though, most distros are working at different goals. It can't really be said that Ubuntu wins against Slackware, as Slackware is not trying to be the things Ubuntu is trying to be.

I agree that Ubuntu is the best choice for new users. That is also why I'm "on board". ;-)

> **aeklabunde said:**
> This has been a fun discussion, and  I look forwad to becoming more comfortable with command line in the coming months. And I know to come to you when I've got questions, ..so Thank You! I'm sold on Ubuntu, and look forward to each new release!

Yeah, I've enjoyed myself and I've greatly appreciated your perspective. :-D

It's easy to forget how important a good GUI is when you're working on "mastering" the command line.

> **aeklabunde said:**
> Thanks for the insight about gOS!  I should be setting up the system in the next few days, and I'm looking forward to it!  Also, I'll post a new thread about the VIA CPU when I get a chance.  Right now, it's dinner time!

I hope that dinner was wonderful! :-D

---

### Post by simon.a.ruiz on 2008-04-28
> **aeklabunde said:**
> I still shy from command line, though I use it from time to time with ffmpeg.

Wow, yeah, ffmpeg is one doozy of a command-line util...

---

### Post by tommygm on 2008-05-07
This being my first post , just wanted to say hello. I am life long resident of Peru and have been using Ubuntu  off and on for -- I think about a year. 
As I type this my pc  that has Ubuntu is upgrading to 8.04 , even with cable access it looks like it will take awhile.
Any way just wanted to let you know that there are a few users in Clown town

---

### Post by simon.a.ruiz on 2008-05-08
tommygm: Awesome. Great to have you!

What's this about "Clown town"? :-)

---

### Post by tommygm on 2008-05-09
Simon , Peru,Indiana was the winter home to several circus troops,dating back to the 1900's maybe earlier . 
We have a amateur circus that all performers are school age up to I think 21 yrs . They were trained by adult circus performers who had retired here . Most if not all have passed on so now training comes from volunteers who them selves performed in the circus.
The clown town name refers to our civic leaders ( we are being lead by clowns), but there is not enough space to go into that .
[http://www.perucircus.com/](http://www.perucircus.com/)
[http://www.cityofperu.org/Circus%20History.htm](http://www.cityofperu.org/Circus%20History.htm)

But seriously the kids do a great job as do the adults who donate there time. 
there have been a couple acts that have traveled to Monaco to perform  for the  King.

---

### Post by simon.a.ruiz on 2008-05-10
Heheh, cool.

I never knew. :-)

---

