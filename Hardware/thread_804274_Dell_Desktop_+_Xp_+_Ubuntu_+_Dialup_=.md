---
title: "Dell Desktop + Xp + Ubuntu + Dialup =?"
date: 2008-05-23
forum: Hardware
---

### Post by cmarlow on 2008-05-23
Hello Everyone,

   I have a Dell Dimiention e521

2 gigs of ram and xp home and ubuntu on another partition.....

 Ok heres the thing I have  Conexant Dialup modem and I can NOT figure out ofr the life of me to get it to work. The reason I am needing to get it tow ork is doing the whole moving thing soon and so I might NOT be in an area of HSI ( High Speed Internet ) SO I guess its good to be best to get that to work.

   SO I went to the linux.dell.com and downloaded the .DEB file for ubuntu 7.10 Conexant driver.. Double clicked on it.... I let it run but it says that as a status something about its the same driver or something like that... So I am wondering if I could get some step by step on how to get it working

Thanks,
Christopher

**EDIT**

I also had GNOME-PPP installed also!

---

### Post by cmarlow on 2008-05-24
[size="7"]*bump*[/size]

---

### Post by prshah on 2008-05-25
> **cmarlow said:**
> Hello Everyone,
   I have a Dell Dimiention e521
 Ok heres the thing I have  Conexant Dialup modem and I can NOT figure 


Step 1: is the modem recognized? ```
lspci | grep -i modem
``` Mine gives me "Smart Modem... Unknown" etc.

---

### Post by cmarlow on 2008-05-25
> **prshah said:**
> Step 1: is the modem recognized? ```
lspci | grep -i modem
``` Mine gives me "Smart Modem... Unknown" etc.

I can copy and paste that command in Terminal just like that?

Ok I just ran this from the LIVE CD that command you gave me and this is what came up..... Please see the attached image!

Thanks!

---

### Post by prshah on 2008-05-25
> **cmarlow said:**
> 
Ok I just ran this from the LIVE CD that command you gave me and this is what came up.....

Looks recognized enough to me. Now, in the same way (terminal) this command's output please? Don't need to do it from the live CD though, your ubuntu installation will do just fine, but whatever you prefer

Step 2:
```
dmesg | grep -i -A 3 -B 3 ttys
```

---

### Post by cmarlow on 2008-05-25
> **prshah said:**
> Looks recognized enough to me. Now, in the same way (terminal) this command's output please? Don't need to do it from the live CD though, your ubuntu installation will do just fine, but whatever you prefer

Step 2:
```
dmesg | grep -i -A 3 -B 3 ttys
```

Nothing happened when I did that.... Check out the attached image

I will have to install ubuntu today I was waiting to make sure my modem was going to work before I did...

---

### Post by cmarlow on 2008-05-25
well we know that stuff works so what do I have to do to get the modem installed?

GNOME-PPP still says theres no modem onboard when I try to auto detect.

---

### Post by prshah on 2008-05-26
> **cmarlow said:**
> well we know that stuff works so what do I have to do to get the modem installed?


If your modem is set up properly, it should create a corresponding ttySxx device in /dev/. That device is probably not being created, in which case there is no way to access the modem.

Why is the device not created? Looking into it...

Can you post your entire dmesg as an attached file? Just type ```
dmesg > dm.txt
``` and then attach the dm.txt file.

---

### Post by cmarlow on 2008-05-26
> **prshah said:**
> If your modem is set up properly, it should create a corresponding ttySxx device in /dev/. That device is probably not being created, in which case there is no way to access the modem.

Why is the device not created? Looking into it...

Can you post your entire dmesg as an attached file? Just type ```
dmesg > dm.txt
``` and then attach the dm.txt file.


I did the >dmsg dmsg.txt

but theres no file

ALSO....... When I did dmesg | grep -i -A 3 -B 3 ttys

there was no output no error message or anything  as you see in the picture it just went back to ~ubuntu@ubuntu: command line like it was ready for something else

I even installed the HSF DRIVERS.... FOR the modem from LINUX.DELL.COM

says on the status: SAME VERSION ALREADY INSTALLED

:( 

~ Christopher ~

---

### Post by cmarlow on 2008-05-27
> **prshah said:**
> If your modem is set up properly, it should create a corresponding ttySxx device in /dev/. That device is probably not being created, in which case there is no way to access the modem.

Why is the device not created? Looking into it...

Can you post your entire dmesg as an attached file? Just type ```
dmesg > dm.txt
``` and then attach the dm.txt file.


Hello are you still here? I havent heard from you in 2 days :confused: :( ??????????????????

---

### Post by cmarlow on 2008-05-28
*sigh* Im starting to give up.. I dont understand how to get this modem to work :\

the dude that was helping me just quit. I havent heard from him in 3 days

---

### Post by prshah on 2008-05-28
> **cmarlow said:**
> *sigh* Im starting to give up.. I dont understand how to get this modem to work :\
the dude that was helping me just quit. I havent heard from him in 3 days

I really don't know how to put this to you politely, so I thought it's better to remain silent. Now however;

Did you even bother to understand the command I had asked you to do? "dmesg > dm.txt"? If you had taken the trouble, and the 1 extra minute to understand what it should do, you could have by now found about a million different ways to do what I'd asked. That information is _vital_ and no one can hope to solve a problem like this (if indeed an actual problem exists) without more information than some vague generalizations and lies:

> 2 gigs of ram and xp home and ubuntu on another partition.....
> 
I will have to install ubuntu today I was waiting to make sure my modem was going to work before I did...

I'd be happy to help you out here, except that you are not co-operating at all. Can you spot the difference between the command I asked and your reply:
> 
```
dmesg > dm.txt
```
> I did the >dmsg dmsg.txt

If I can take the time and trouble to be specific, why can't you? Even with the best of intentions, I cannot help you if you persist in being vague or inaccurate.

To get back on track.. if you still want to... post the output of your dmesg command.

---

### Post by cmarlow on 2008-05-28
> **prshah said:**
> I really don't know how to put this to you politely, so I thought it's better to remain silent. Now however;

Did you even bother to understand the command I had asked you to do? "dmesg > dm.txt"? If you had taken the trouble, and the 1 extra minute to understand what it should do, you could have by now found about a million different ways to do what I'd asked. That information is _vital_ and no one can hope to solve a problem like this (if indeed an actual problem exists) without more information than some vague generalizations and lies:





I'd be happy to help you out here, except that you are not co-operating at all. Can you spot the difference between the command I asked and your reply:



If I can take the time and trouble to be specific, why can't you? Even with the best of intentions, I cannot help you if you persist in being vague or inaccurate.

To get back on track.. if you still want to... post the output of your dmesg command.


well LET ME PUT IT TO YOU NICELY...... In the nicest way....

   I told you if you would look back a couple posts I typed in the dmsg > dmsg.txt and it did not make a file all it did was go back to the Terminal prompt. 

ive been waiting on you for the next step.... SO theres no need to get rude when Ive been posting screenshots and everything for you to check out.

I even posted WHAT HAPPENED and it just went back to the next terminal prompt line.

AND I QUOTE:
=====================
I did the >dmsg dmsg.txt

but theres no file

ALSO....... When I did dmesg | grep -i -A 3 -B 3 ttys

there was no output no error message or anything as you see in the picture it just went back to ~ubuntu@ubuntu: command line like it was ready for something else

I even installed the HSF DRIVERS.... FOR the modem from LINUX.DELL.COM

says on the status: SAME VERSION ALREADY INSTALLED

 

~ Christopher ~

--------------------------------------------------------------------------------
Last edited by cmarlow; 2 Days Ago at 05:18 AM.  
      


Theres proof in those entries... back on page 1

---

### Post by cmarlow on 2008-05-28
I'd be happy to help you out here, except that you are not co-operating at all. Can you spot the difference between the command I asked and your reply:


If I can take the time and trouble to be specific, why can't you? Even with the best of intentions, I cannot help you if you persist in being vague or inaccurate.

To get back on track.. if you still want to... post the output of your dmesg command.[/QUOTE]
-----------------------------------------------------------------


OH, REGARDING THAT:

I copied and pasted what you said into the terminal. the whole DM > DMSG.TXT command thats how I have been doing all the commands you have been asking me is that not right what am I doing wrong?

---

### Post by prshah on 2008-05-28
> **cmarlow said:**
> 
dmsg > dmsg.txt
> 
I did the >dmsg dmsg.txt



> **cmarlow said:**
> 
 DM > DMSG.TXT

```
dmesg > dm.txt
```

Can you _still_ not spot the difference? You claim to have run three different commands, all three of which are wrong. And if you have _actually_ copy and pasted the above command in a terminal, it _will_ produce a file with the filename that follows the ">". If it _doesn't_ create a file, you're doing something wrong.

Considering rudeness, I did tell you there was no way for me to say it nicely, which is why I decided not to say anything at all. Now that you feel that I'm all rude and crude, maybe you need someone else to help you out; someone who is more capable than I am.

Cheerio!

---

### Post by cmarlow on 2008-05-28
> **prshah said:**
> ```
dmesg > dm.txt
```

Can you _still_ not spot the difference? You claim to have run three different commands, all three of which are wrong. And if you have _actually_ copy and pasted the above command in a terminal, it _will_ produce a file with the filename that follows the ">". If it _doesn't_ create a file, you're doing something wrong.

Considering rudeness, I did tell you there was no way for me to say it nicely, which is why I decided not to say anything at all. Now that you feel that I'm all rude and crude, maybe you need someone else to help you out; someone who is more capable than I am.

Cheerio!

I guess the truth hurts.....I hate to say it but you were kinda rude first by what you said. Just your tone in your message sounded rude. instead of taking time to help someone and walking them step by step you get PISSED OFF if they do something wrong and SNAP BACK at them.

And by the way what I said was.....I was merely saying theres no need in being rude when I am a noobie and am trying to learn this. I wasnt calling you rude.But.. after that message YOU ARE RUDE.....

IM SORRY TO TELL YOU LIKE IT IS... BUT you were rude....

AND YOU WONDER... why people stick with MS WINDOWS. its rude ppl like you

TA TA!

---

