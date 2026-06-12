---
title: "What is a &quot;Super User&quot; ??"
date: 2008-07-04
forum: Hardware
---

### Post by Ashejoe on 2008-07-04
My system is running Ubuntu 8.04.

I downloaded the "supposed" Linux drivers for my ATI 9600 "All-In-Wonder" graphics card from the ATI website.

I go to install it, and get rejected with some vague statement saying that only a "Super User" can install this software. 

What is that supposed to mean ???

"I" and "I ALONE" am the sole and only person who uses this computer.  There is no "System Administrator";  There is no "Root User".... only "ME".

So how am I suppose to install this thing ?

---

### Post by tamoneya on 2008-07-04
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Ashejoe on 2008-07-04
WOW...... I only posted that request 4 minutes ago and I've already got a response !!  THANK YOU !!!  (hold on, let me pick myself up off the ground !!! :lolflag:)

I'll give it a try.

Tell me this:
I tend to share the feelings of many users who've tried Linux... and that is how frustrating it is to install software that IS NOT part of the official repository !   (Humbly I say that's what always sends me scurrying back to Windows... is the inexcusable difficulties trying to install Linux software.) 

We go in and "attempt" to search for information, but, if you don't know the exact name or term,  as well as the precise spelling.... your search comes up empty.  

I realize there are many "flavors" of Linux out there.  Some use the "rpm" format, others the "tz" format, ect.  

Is there any kind of WELL ILLUSTRATED (as in "lots of screen shots") page that shows screen by screen how to install such software ?  For example, I've been trying to install the video program Cinerella as well as OpenOffice 3 Beta, which are not part of the official Ubuntu repository.

Thanks again for the prompt reply.  I really do sincerely appreciate it.

---

### Post by Ashejoe on 2008-07-04
Well, once again I find myself on the brink of going postal with the never ending hassles of installing software in Linux.

OK, I did as you stated, and the thing still refuses to initiate an installation !  (surprise, surprise.......)

I open the SHELL - KONSOLE window, and type in the following command line to no avail:

Athlon:~$ sudo ./ati-driver-installer-8-6-x86.x86_64.run

I'm in the desktop where the file downloaded to.  Yet, all I get is "command not found"

Gawd why does this thing have to be so freakin difficult ?

---

### Post by tamoneya on 2008-07-04
> **Ashejoe said:**
> Well, once again I find myself on the brink of going postal with the never ending hassles of installing software in Linux.

OK, I did as you stated, and the thing still refuses to initiate an installation !  (surprise, surprise.......)

I open the SHELL - KONSOLE window, and type in the following command line to no avail:

Athlon:~$ sudo ./ati-driver-installer-8-6-x86.x86_64.run

I'm in the desktop where the file downloaded to.  Yet, all I get is "command not found"

Gawd why does this thing have to be so freakin difficult ?

please run in the directory containing the file and post the output off: ```
ls -l
```It may be that you dont have executable permissions on the file.  In terminal you can copy with ctrl-shift-c.

---

### Post by Ashejoe on 2008-07-04
Tell you what, I've already taken my frustrations with this out on my kids, so would you please be so kind as to just give me a line by line description of:

 
1)  How do I get to the desktop where the file downloaded ?  (I already have KONSOLE opened)

2)  The command line I should give it to make the installer work.

Please don't assume that I (or anyone else reading this post) is as knowledgeable and Linus Savy as you are.

Sorry, but I continue to get to the point of such total frustration with what an inexcusable HASSLE it is to install software in Linux.

Thank You

---

### Post by tamoneya on 2008-07-04
provided you have the file on the desktop the full set of commands would be:```
cd ~/Desktop
sudo ./ati-driver-installer-8-6-x86.x86_64.run
```
Make sure you have a capital D on "Desktop"

---

### Post by Ashejoe on 2008-07-04
IT WORKED..... IT WORKED.... IT WORKED.... YEEEEE HAAAAA  IT WORKED  IT WORKED !!!

THANK YOU THANK YOU THANK YOU..... and my kids thank you also now that dad's not as grumpy and has promised to take them for ice cream !!!!  WE ALL THANK YOU:guitar:

And following your advice....I think I know what I was doing wrong;

Actually, I was doing what you suggested... and it refused to work. 

I believe the reason was that when my first download of the ATI drivers failed to download properly, the second download assigned the name "...x86.x86_64(2).run"

When I went in and renamed named the file by deleting that "  (2)   ", the installer worked !

Thank you for putting up with my frustrations.

---

### Post by 16777216 on 2008-07-04
Installing software in Ubuntu is usaly not difficult but you need to know a few things about how linux does things.

1: The command line is case sensitive, for example "Command" is not the same as "command".

2: All files have permissions that tell the owner and the group and if each or others can read, wright, or execute the file.

3: Their is **always** a root user who is the administrator.

( If any one would like to add/correct this feel free. )

( Nevermind the part below you just were mistaken on the file name. )

Now it sounds like the file is not marked executable, right click on it and choose properties in the popup menu.
Next, click the permissions tab and click the "Allow executing file as program" check box.
Close the window and try again.

And yes, I agree compiling from source can be a pain sometimes.

---

### Post by issih on 2008-07-04
Unfortunately once you go "off reservation" and leave the comfort of repositories and .deb files things can get difficult when it comes to installing things. There is no point blaming ubuntu for this however. It is perfectly possible to distribute windows software as source files, and I assure you, you would have a hell of a time getting that installed too.

The fact is that the current monopoly held by windows means it is economically sensible for every hardware company under the sun to write and distribute compiled drivers for the windows platform. It isn't viable for them (or they can't be bothered) to support linux in the same way. This is complicated by the fact that linux as a whole has no unified method of packaging software that all the distos agree on.

It is perfectly possible for someone to take the source code, compile it, turn it into a deb file and upload it to a repository.

This is ALWAYS true,it just hasn't been done because nobody invested the time, money, hardware, whatever to achieve it for te specific bit of software that you want.

Pain in the but yes. But not something that can be fixed by ubuntu. The only solution is if ubuntu grows large enough to force hardware manufacturers to take notice and start shipping compiled .deb files.

Simple reality is that ubuntu's methodology for installing, packaging and managing software is actually vastly superior to that of windows. Unfortunately the hardware manufacturers drop you in at the deep end with no life raft instead of providing you with a nice little speedboat, they easily could provide software for ubuntu that is as easy to install as it is for windows, be it via deb files, or their own repository. The mechanisms exist for software to be delivered to you easily, you can't really blame ubuntu if the hardware manufacturers can't be bothered to use it.

---

### Post by Ashejoe on 2008-07-04
Thanks ISSIH for your advice.

Actually, although I WAS extremely frustrated, I made every attempt in my posts to say "Linux" and not "Ubuntu".

Truth be known, I actually have an incredible amount of admiration for the entire Ubuntu community.  That admiration grew even greater when I read about the Internet Billionaire who funded the Ubuntu project.  

And,(believe it or not), I actually prefer Ubuntu over Windows for what I do most... web surf / email / and on-line applications, such as [www.zoho.com](www.zoho.com). I feel a whole lot safer going out onto the world wide web with Ubuntu than I do Windows XP.

Having said that though, there are several programs that have really frustrated me in my attempts to install them.  For example, I'd like to edit my many VCR videos onto DVD's.  The only "Linux" program that seems to be able to do that is Cinerella.  Try and install that one !!!!

OK, I'll get off my soapbox now.  Thank you all once again for your patience with me.

---

### Post by tamoneya on 2008-07-04
if you are really feeling boxed in by the lack of linux software you should try using wine.  This allows you to run windows applications in linux.  Then you can run whatever windows program you used to use inside linux.  CS3 is currently not supported but CS2 apparently works very well.

---

### Post by jocko on 2008-07-05
> **Ashejoe said:**
> Having said that though, there are several programs that have really frustrated me in my attempts to install them.  For example, I'd like to edit my many VCR videos onto DVD's.  The only "Linux" program that seems to be able to do that is Cinerella.  Try and install that one !!!!

Cinerella provides an ubuntu repository, so it shouldn't be that difficult. [Here are their instructions]("http://cinelerra.org/getting_cinelerra.php#hardy") for adding it to your software sources. Just follow those instructions to add the repo, then use synaptic to install cinerella.

---

### Post by Ashejoe on 2008-07-05
Thank You Tamoney and Jocko.  

I can't begin to tell you how humbled I am with your patience with me.  Wow, I never experienced such sincere support like this in my past Linux exploratory journeys with Mepis, SuSe, or Fedora !  This Ubuntu community truly is "unique"... not "geek".... if you know what I mean ?

WINE:  Yes !  Super, super, super.  I installed it and it actually did allow me to run some of my favorite old Windows programs.  And shockingly, (for me at least), it turned out to be easier to install and to use than I thought it would be.  Fantastic tip.  Thanks !!

CINERELLA:  OK, as soon as I thank you for the tip Jocko, I'm headed to that link to try it out.  Sounds like it's going to be well illustrated... which is precisely what I need at this stage of my Ubuntu experience.  Thanks again.

I really don't know what else I can say except that I am very humbled by all of the sincere and genuine help I've been getting on this forum.  

It really doesn't surprise me that Ubuntu has been getting so much good press in the media.  With a sincere and knowledgeable support community like this, it's no wonder.  I'm even thinking about taking a more active role in the "community" myself after what all of you have allowed me to experience.  As I said, it truly has been gratifying.

THank You All  ):P

---

### Post by issih on 2008-07-05
A quick google threw this up:

[http://www.ubuntu-unleashed.com/2008/05/howto-install-cinerella-video-editor.html](http://www.ubuntu-unleashed.com/2008/05/howto-install-cinerella-video-editor.html)

sadly there a few command line manipulations necessary to tell ubuntu where the cinerella repository is, and indeed to authenticate with it.

But once that is done you should be able to install it easily.

Best of all, doing it through a repository like this means you will get updates to the program automatically pushed to your machine through the normal update manager, just like every other program ubuntu uses..

Hope that helps, and sorry if I ranted a bit earlier :)

---

