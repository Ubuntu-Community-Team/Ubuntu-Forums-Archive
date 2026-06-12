---
title: "First it was internal modems now wireless cards.........."
date: 2008-05-24
forum: Hardware
---

### Post by angryuser12 on 2008-05-24
I have been using linux on/off for a while now....in the early days the big thing that was holding back linux was not being able to connect to the net because of WINMODEMS..........

now in year 2008, using UBUNTU 8.04 (best linux OS company) on a TOSHIBA TECRA S2 the system won't detect/connect to wireless networks.

I have tried NDISWRAPPER with the driver from ([http://driverscollection.com/?H=Tecra%20S2&By=Toshiba](http://driverscollection.com/?H=Tecra%20S2&By=Toshiba)) and what do i get????

wlan0     No such device

try this, try that........spend the whole day.....got nowhere......nice OS but useless.....

---

### Post by PauGNU on 2008-05-24
Hi

What's your card model?. Open a terminal and type this:
```
lspci
```

Put the exit here, please.

---

### Post by angryuser12 on 2008-05-30
sorry for the late reply....I really want to promote Linux (Ubuntu in particular) and I had or still have a chance trying to convince my friends to use it.

About a week ago I was visiting my friend who lives 600kms away from me. While i was there his laptop (toshiba tecra) broke drown. Windows XP wouldn't work properly....so i downloaded and burnt Ubuntu and installed it..........and it worked beautifully...except the wireless card. My friend said that if I can't access the net using wireless than the laptop is pretty much useless...so I spent my last whole day trying to make wireless work.

I am no expert user, infact i am just a "user" and not a IT or Linux expert. But I hate Windows monopoly and try to convince everyone to use Ubuntu.

So anyway I have come back home and my friend still has the laptop with Ubuntu on it but he is new to linux. So whatever help people offer, I have to simplify it and email my friend to try it out.

So please be patient for my replies and try to give clear and concise instructions.

Thank You.

P.S. I have emailed my friend with these instructions and waiting upon his reply:

OK, this is what the other person is asking for ([http://ubuntuforums.org/showthread.php?t=805572):](http://ubuntuforums.org/showthread.php?t=805572):)

>Hi

>What's your card model?. Open a terminal and type this:
>Code:

  >>lspci



So start up the laptop and put in username hgnis password is drowssap


now go to the first menu in the top left handside...i thinks its the orange icon...and from the first menu (i think it is "Accessories") select
"X Terminal" or something like that it should have a computer with a black screen icon next to it...

now a window should open up which looks something like windows cmd window....

now type in:

    lspci [press enter]
   
and copy and paste the result to me...if theres a lot of crap then try to find the bit about Wireless card....

if you get a message saying something like access denied then do this:

    sudo lspci [press enter]
   
and then simple type in the password and [press enter]

its probably a good idea to plug the internet into the laptop so u can copy and paste stuff from/to the email from/to the terminal window.


And that is our first step...

what u send me i'll put it on the discussion board and wait for the other person to reply.

thanks.

bye.

----------------
I have put up my instructions so that if I am doing something wrong please tell me.

---

### Post by angryuser12 on 2008-05-30
ok this is what my friend says:

>>>> bash: Ispci: command not found

---

### Post by angryuser12 on 2008-05-30
Sorry about that..I just relised that he typed in Ispci and not lspci

bloody fool.....

---

### Post by ugm6hr on 2008-05-30
It might be sensible to get as much info as possible at once from your friend, rather than going backwards and forwards.

Once he's figured out Terminal (sounds like he has) - point him here: [http://ubuntuforums.org/showthread.php?p=5024425](http://ubuntuforums.org/showthread.php?p=5024425)

Then report back with all the details.

---

