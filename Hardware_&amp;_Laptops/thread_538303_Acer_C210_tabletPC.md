---
title: "Acer C210 tabletPC"
date: 2007-08-29
forum: Hardware &amp; Laptops
---

### Post by ldesilva on 2007-08-29
Hi all,

I am new with Linux. I am wondering has anyone installed Ubuntu on the Acer C210 tablet?

Any gotcha that I should be aware of?

Thank you in advance.

---

### Post by cbanbury on 2007-08-30
Hi, 
I recently got a Acer C210 and so far this is what I have managed to get working...

Almost everything works out the box, including the pen, apart from: 
-fingerprint reader, install thinkfinger to get it working 
-Suspend needs configuring for the nvidia drivers before it will work
-rotate screen works, but haven't found out how to map it to hardware keys + stylus orientation remains in normal mode...grrr
-Have yet to find a writing pad but haven't really looked tbh 

The only other problems Ive had are with software. I really miss having Microsoft OneNote and Alias sketchbook. 

Please let me know if you need any support getting the above working, I know I spent ages trying to do little things so if I can help I will :)

---

### Post by ldesilva on 2007-08-30
Hi cbanbury,

Thank you for the information. By the way, where can I download the thinkfinger and how do I configure it?

Cheers,
L

---

### Post by cbanbury on 2007-08-30
There is a howto for thinkfinger here: 
[http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger](http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger)

If you follow it exactly you will be fine. I say that because I didn't...and got myself in a world of trouble :p good luck! 

If you or anyone else finds a way to get the screen rotate to work with rotating the pen/stylus please let me know...giving me quiet a headache atm

---

### Post by ldesilva on 2007-08-30
Thanks.

---

### Post by cbanbury on 2007-08-31
Ok screen rotation (with the stylus) is now working! 

Finally got it working, so thought I would share. Turns out to be a really simple solution but hey. 

[http://www.gottabemobile.com/forum/forum_posts.asp?TID=1012](http://www.gottabemobile.com/forum/forum_posts.asp?TID=1012)
Has instructions for making the .sh files to change the screen orientation and enabling 
rotation with for the nvidia driver. 

Can't map it to a hardware key yet, just got icons on my taskbar for portrait and landscape mode. 
When I tried to map to the screen rotate button found none of the three hardware keys work :(
That is ubuntu doesn't even acknowledge them being pressed...at all! 

Let me know if you need anymore help getting anything working, hopefully that should make things easier for you. Good luck!

---

### Post by ldesilva on 2007-10-11
Hi cbanbury,
Just installed Ubuntu 7.10 RC onto my C210. Everything seems to work but the there is no sound. :(

Haven't got the fingerprint working yet. looks like it is a tedious things to do. And yes, the hardware buttons no work either.

By the way, have you found any good applications for the tablet yet? Like you said, really miss the OneNote. By the way, do you know how do I get the onscreen keyboard display? (or is it available in Ubuntu)

Any other applications that I can use the stylus will be handy?

Thanks.

---

### Post by cbanbury on 2007-10-13
Hi ther,

I am ashamed to say that I was forced to go back to windows shortly after writing my last post :( 
However I'm going to hav a play with 7.1 when its released :D 

As far as sound is concerned, as far as I can remember ubuntu just puts the wrong master control by default. All you need to do is open up ur sound setting menu and find the correct control (think its 'Front'). 

Let me know if that sounds like gibberish and il help some more. 

With applications, I went back to windows because I couldn't get Onenote to work, as far as I'm concerned its the best tablet application and I just can't do without it! 

There is a on screen keyboard application already in ubuntu, can't remember the shortcut for it, but it is there. 

Sorry I can't be more specific, il be more help once I got 7.1 up and running on my tablet :D I'm really hoping to get the hardware buttons working this time

---

### Post by ldesilva on 2007-10-13
Ok. I am using 7.10 RC now and got the sound working from [http://ubuntuforums.org/showthread.php?t=202555&page=5&highlight=Intel+HDA](http://ubuntuforums.org/showthread.php?t=202555&page=5&highlight=Intel+HDA)

I am still having problem trying to configure the fingerprint. I do not have much knowledge with linux. sigh. :(

---

### Post by cbanbury on 2007-10-16
Did you follow the HOWTO link for the fingerprint reader that I posted? Tell me where you get stuck in that and I can help you further. Otherwise I'm taking a bit of a ball park guess as to what your doing wrong.

Btw, would you mind telling me how your finding v7.1? 
How long is the boot time? 
Does suspend work out the box? 

Also could you please open up a terminal and run 'xev' (obviously without the quotes). From what  I remember you should see a bunch of text come up for every piece of hardware you use. So don't touch anything else, apart from the tablet buttons (i.e. screen rotate). Can you tell me if xev shows any output when you press these buttons? 
(don't worry about what the output is, I just want to know if there is any) 

Thanks in advance 

Stick at it! (thats more of a note to me than anyone else :P)

---

### Post by ldesilva on 2007-10-16
> **cbanbury said:**
> Did you follow the HOWTO link for the fingerprint reader that I posted? Tell me where you get stuck in that and I can help you further. Otherwise I'm taking a bit of a ball park guess as to what your doing wrong.

Btw, would you mind telling me how your finding v7.1? 
How long is the boot time? 
Does suspend work out the box? 

Also could you please open up a terminal and run 'xev' (obviously without the quotes). From what  I remember you should see a bunch of text come up for every piece of hardware you use. So don't touch anything else, apart from the tablet buttons (i.e. screen rotate). Can you tell me if xev shows any output when you press these buttons? 
(don't worry about what the output is, I just want to know if there is any) 

Thanks in advance 

Stick at it! (thats more of a note to me than anyone else :P)
It takes less than 1 minute to start.  The buttons next to the screen does not work (ie screen rotate). But the web browser and mail button works :)

Can suspend the machine but when bring it back from suspend, a black screen. I know hibernates work :)

Really like the 7.10 (since it is only RC). able to write to NTFS :)
But I couldn't get VMWare server starting a VM if it is stored on the usb drive :(

one more thing I found on the Desktop Effects, the nvdia driver is not working properly. the screen flashes every now and then. i have disable desktop effects now. if u get it working without screen flashes, let me know.

I got the fingerprint working. follow another article ([http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_Beta_on_a_ThinkPad_T61]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_Beta_on_a_ThinkPad_T61"))

Oh ya, how do I un-install an application if it does not appear in Synaptics? For applications that i install using the ./install.pl

How do I stick it?

---

### Post by cbanbury on 2007-10-17
Sounds promising overall! Bit of a git that the hardware buttons on the screen don't work tho :( 

Suspend I remember being a very easy one to fix, its to do with your nvidia driver and you have to add a line to the xorg.conf file. 
Again off the top of my head it was something to do with 'AvGP' but can't remember exactly what it is. 

Sorry can't help with vmware but for compiz I you will need to use 'AGILX' (again to do with the graphics card).

I'm sorry the above are abit hazy, but its bin ages since I was facing these problems :P just search for those words etc and u'l find the answer out there! 

I would have thort that for removing programs that were installed using ./install.pl just remove all of the related files :) 

And ye, u gota stick with ubuntu! Don't get going back to the dark side like I did (aka Windows!!) Just think that remember your not seeing any dreaded blue screens of death...or*ding*  'Windows has encountered an error'  hehe

---

### Post by ldesilva on 2007-10-17
got vmware working on my external usb drive. it is a known issue when try to access ntfs partition. :)

hehe. when you get yourself back onto ubuntu, perhaps when u resolve the suspend and the compiz fusion issue, you can advise me on exactly what to do. :)

---

### Post by cbanbury on 2007-12-17
Hi! 

Sorry for taking so long, but finally plucked up the courage to put Gusty on. How many of you are still at it? 

Well so far I have wot I had working before, only I can now right to NTFS (Yipee!).

Anyone figured out how to get the three buttons on the screen working yet?

---

