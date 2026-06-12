---
title: "New Radeon r9 270x graphics card, black screen"
date: 2014-03-23
forum: Hardware
---

### Post by MacCrackizWhack on 2014-03-23
Several questions. I bought used a dell xps 9100, several years ago.   Installed Ubuntu and Kubuntu and have updated to saucy. At a certain point, Kubuntu would no longer boot, I would get a message, don't quite recall, something about q-bus shall I try d-bus. I found Xfce would work, so I started to use that. Very often, small square dots would appear all over the screens, when looking a webpages or pictures, sometimes then the machine would freeze. In windows the same thing started to happen, although windows would restart the graphics, so I did not have to turn off the machine and re start. I assumed then it was a hardware issue.  Yesterday I bought a Radeon  r9 270x, and put it in the machine. Booted into windows, which went to a low graphics mode, put in the cd, (cd player has been very squirrly also, I was surprised it worked) all good on that. So going into ubuntu i am getting a black screen. I went into recovery mode, but no luck with fail safe graphics mode. I just get a black screen. Got into the terminal mode there, had some limited success, did a few operations, used some of the utilities there, I was able to download the latest beta drivers from the AMD site in the terminal there, but did not have success installing them. For reasons above my understanding it ran through many operations, but did not install. Also saw an interesting note about this operation making a 'taint' on the kernel, which did not sound good to me.  Now, I can take the card back to the store, I spent about $200 on it. Perhaps a nvidea card would be better? Thing is, I don't actually think my problem is the card, at this point. Should not the graphics fail safe mode work?  I had the radeon 5970 2gb which other than the snowflake problem, was satisfactory. I had two screens, wanted a third to use in a package only available in windows, which I why i got the r9 270x, probably overkill.

---

### Post by MacCrackizWhack on 2014-03-23
So I put the old card back in. It boots the login screen, with the interference/snowflakes/noise. but just for a moment, then goes black. This is the same thing it did with the new card, would take me to the login prompt, then a few seconds later, go black. So I am really stuck now. So now I am thinking the card is only tangentially related to the underlying problem, which also makes me think my question may be better in another forum possibly. To sum up, I was already having log in /boot problems, but now with the new card, and whatever I may have done, I am unable to get in at all, with the exception of the command line through the recovery mode. But the windows side works fine, whereas before, it did not, fwtw.

---

### Post by Mark Phelps on 2014-03-23
>  I was able to download the latest beta drivers from the AMD site in the terminal there, but did not have success installing them. 

Sorry, but the AMD R9 fglrx drivers are not "ready for prime time" yet.  At this point, all you can do is use the generic Radeon drivers.

To remove the fglrx drivers, read through the material in the link: [https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by MacCrackizWhack on 2014-03-23
Well I don't know what it was, but seems to have worked, though as I say, I have put the original card back in the machine. And somehow the original problem of the snowflakes has disappeared. Perhaps the act of removing and replacing the card was all that was needed. The black screen occurred before I did anything to the system, aside from putting in the new card.  It was going into the recovery mode that I tried different things, with no success.  The AMD drivers were never successfully installed. I did do the apt-get remove, confirmed that fglrx was never installed, but I did remove the DKMS modules in that operation. (I really don't know what I may or may not have installed. Just trying to type in the commands that seem reasonable)  I did not have success with those other commands, after many tries, but I did go and do apt-get update.  I got to the text login, and logged in, which is an improvement over a black screen. rebooted from there, somehow I am now back in. As I said, I put the old video card back in, the screen is perfectly clean, no snowflakes, etc., I now wonder if the act of removing and replacing has cured one of the  original problems. Now, attempting to log into the kde plasma desktop. First it says system error. Then I get this message: could not start D-bus. Can you call qdbus? ok. then nothing. then back to the login.

---

### Post by MacCrackizWhack on 2014-03-23
New update: Working on the machine, I had put the DVI cords for the two monitors in reverse, than what they were, as I was crawling around beneath the desk.  I just now reversed them, and the noise/snowflakes are back. Reverse them again, and now the screen is clear. Odd. Does anyone have any insight on this?

---

### Post by MacCrackizWhack on 2014-04-13
Still stuck on this. I used the gui in with the old card, did what I thought was enough, and put the new card in, booted to black screen. Now I have done what I thought would remove and replace, to no avail. I have tried numerous operations,  at this point, the LSCI command replies 'can't open display' No luck either with ./* --initial either with aticonfig or amdconfig.

---

### Post by MacCrackizWhack on 2014-04-13
Sorry, meant LSPCI.  Followed the instructions on wiki.cchtml.com   Installed 
catalyst-14.3beta1.0 to my saucy 13.10.  

I have two monitors, finally figured out to turn one off. The sound was on, so in the next boot, I waited for the bongo. The screen was black when I did this. 
  I entered the password, and waited. In a minute I was in. Victory! From there it was possible to make the monitor adjustments from the settings menu, A and R, I believe its called,  and get both working again. I rebooted, and everything seems to be fine. In the AMD catalyst manager, there was also a check to enable d-bus. I will see if this solves my kubuntu problem.  No idea how this would have become un-checked. 

As I indicated, it was necessary to install and delete the drivers at least three times. I add this for persons who may be confused about these things as much as I am.  I am sure I spent at least two to three full days fooling with this, reading and trying commands. I think I was just lucky, in the end. that and the packages have their own magic built in. To be fair, I have no idea what this thing is currently running. But it does seem to be working.

---

