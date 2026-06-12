---
title: "ATi 1950 Pro cooler spinning.."
date: 2008-02-19
forum: Hardware &amp; Laptops
---

### Post by KenTor on 2008-02-19
So here is the deal ..
 I've been trying make this work since .. lets saaaaaaay .. December 2006? 
my problem is that from the first computer i bought until now i've been using ATi .. 
And i like that .. but not when it come to ubuntu ..

Right now i have:
[B]C2D E6400
2gb Pc6400 ram
40gb harddrive for Ubuntu
and finally my Ati Radeon 1950Pro 256mb GDDR3..[/B]

i dont have any problems with running ubuntu .. 

Actually this is my last call for help .. 

The problem is my Graphic Card.. When i install ubuntu everything is running fine .. but then i have to install the GFX driver for the gaming .. 
 but when i install a driver for the GFX, the cooler begins to spin and i think that my GFX gets warm too .. 
I have tried ALL The drivers i could find on the internet .. nothing helps .. 

So plz .. if anyone .. ANYONE .. knows how to fix this, I would be SO thanksfull :/

 This is the only thing that's keeps me away from ubuntu .. 
 I use ubuntu on my laptop and my mothers computer ..

but I cant seem to make it work on my own computer ..


Hope someone can help.. As i said .. last call for help :(

/ thanks

---

### Post by Fechter on 2008-02-19
Well, you have some options. Supposing you are using a Sapphire ati VGA- Sapphire have always made good Ait's but unfortunately with not so good fans- same as Asus.
So if you don't mind I can recommend you some other coolers:) 
If you prefer active cooling/with fan/
[http://www.newegg.com/Product/Product.aspx?Item=N82E16835118011](http://www.newegg.com/Product/Product.aspx?Item=N82E16835118011)
This I think is very good. If you prefer passive cooling/without fans/
[http://www.newegg.com/Product/Product.aspx?Item=N82E16835118029&Tpk=Zalman%2bVNF100](http://www.newegg.com/Product/Product.aspx?Item=N82E16835118029&Tpk=Zalman%2bVNF100)
for your model.

Other options are- enter your BIOS, and look into the cooling options.
Or if there is/ I don't know, supposing/ an Ati control center- adjust the fan settings.

I hope have been helpful.

---

### Post by KenTor on 2008-02-19
Dude :P .. 
I dont want to burn my Gfx :o ..

 It gets warm when im in ubuntu .. In windows it's nice and cold.. :o

---

### Post by Fechter on 2008-02-20
So the problem is in the drivers. I recently read a thread in another forum that the latest Catalyst - I think 8.2 - fixes these kinds of bugs.. have you tried those?

---

### Post by PiggiePaul on 2008-02-20
I found exactly the same with mt ATI X800 pro card.

Like you, the PROPER drivers were overheating the card.

After about 15 mins I started betting random green pixels over the screen (like a snow) then the screen would start flashing off and on again, and if you then left it another 10 to 15 seconds you'd loose the screen totally.

Like you, I also heard my fan kick into high speed, which it NEVER does, only for some VERY intense parts of 3D games.

I thought I'd fried it, as the 1st time (when I lost the screen) I did not even have ANY display when I rebooted, not even from the BIOS screen !!!!!

After a few mins off, all was OK again.

Now, I've just not installed any drivers (only what ubuntu gives you during installation) and ignored the popup about drivers when you do your 1st boot up.

compiz and all the 3D cube runs fine, and smooth.

Poss games would need a REAL driver? but not tried any yet.

I've love to hear this has been fixed.

There can be no other conclusion, other than the drivers were overcloking my card.......

---

### Post by KenTor on 2008-06-10
> **PiggiePaul said:**
> I found exactly the same with mt ATI X800 pro card.

Like you, the PROPER drivers were overheating the card.

After about 15 mins I started betting random green pixels over the screen (like a snow) then the screen would start flashing off and on again, and if you then left it another 10 to 15 seconds you'd loose the screen totally.

Like you, I also heard my fan kick into high speed, which it NEVER does, only for some VERY intense parts of 3D games.

I thought I'd fried it, as the 1st time (when I lost the screen) I did not even have ANY display when I rebooted, not even from the BIOS screen !!!!!

After a few mins off, all was OK again.

Now, I've just not installed any drivers (only what ubuntu gives you during installation) and ignored the popup about drivers when you do your 1st boot up.

compiz and all the 3D cube runs fine, and smooth.

Poss games would need a REAL driver? but not tried any yet.

I've love to hear this has been fixed.

There can be no other conclusion, other than the drivers were overcloking my card.......



So you're just running the ubuntu without any driver ?

 Just installed it again, tought maybe all the new updates and stuff would help .. but no, the cooler is still spinning like hell ..



 OP here if any one got other solutions ..

---

### Post by ukripper on 2008-06-17
have you tried installing drivers manually using envy?

---

### Post by KenTor on 2008-06-23
> **ukripper said:**
> have you tried installing drivers manually using envy?


Yea i tried that a couple of times .. 
Still not working .. im so desperate of going for ubuntu and forgetting everything about ubuntu .. but my ******* GFX is not helping me :( ..

 Any other suggestions PLZ ?

---

### Post by ukripper on 2008-06-23
> **KenTor said:**
> Yea i tried that a couple of times .. 
Still not working .. im so desperate of going for ubuntu and forgetting everything about ubuntu .. but my ******* GFX is not helping me :( ..

 Any other suggestions PLZ ?

i am using X1950pro with 512MB mem and temperature stays as normal as in windows.

I am using envy drivers.

Can you do this in terminal:
```
fglrxinfo
```

and post output here

---

### Post by KenTor on 2008-06-23
> **ukripper said:**
> i am using X1950pro with 512MB mem and temperature stays as normal as in windows.

I am using envy drivers.

Can you do this in terminal:
```
fglrxinfo
```

and post output here


Well, i have to install ubuntu then .. 
 going to backup my stuff and give it a try :), 
 will return in one hour..
Thanks



So, after some problems and so im on ubuntu now
the output looks like this:
[B]darwich@darwich:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.1.7415 Release[/B]

installed envy by manual and my cooler is spinning like hell atm.. It's just starts slowly to increase the speed of the cooler .. 
 im not sure if my GFX is getting hot, cant really decide ..

---

### Post by ukripper on 2008-06-23
> **KenTor said:**
> Well, i have to install ubuntu then .. 
 going to backup my stuff and give it a try :), 
 will return in one hour..
Thanks



So, after some problems and so im on ubuntu now
the output looks like this:
[B]darwich@darwich:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.1.7415 Release[/B]l 

installed envy by manual and my cooler is spinning like hell atm.. It's just starts slowly to increase the speed of the cooler .. 
 im not sure if my GFX is getting hot, cant really decide ..

can you install mbmon and check what output you are getting:
```
sudo apt-get install mbmon
```

after it is installed do following:
```
sudo mbmon
```
and post output you are getting.

---

### Post by KenTor on 2008-06-23
> **ukripper said:**
> can you install mbmon and check what output you are getting:
```
sudo apt-get install mbmon
```

after it is installed do following:
```
sudo mbmon
```
and post output you are getting.

darwich@darwich:~$ sudo mbmon
No Hardware Monitor found!!
InitMBInfo: Success
darwich@darwich:~$ 
 
 is what i get ..

---

### Post by ukripper on 2008-06-23
> **KenTor said:**
> darwich@darwich:~$ sudo mbmon
No Hardware Monitor found!!
InitMBInfo: Success
darwich@darwich:~$ 
 
 is what i get ..

have you installed mbmon using:
```
sudo apt-get install mbmon
```
?

---

### Post by KenTor on 2008-06-23
> **ukripper said:**
> have you installed mbmon using:
```
sudo apt-get install mbmon
```
?

Yes, i did install it ..

---

### Post by KenTor on 2008-06-24
OP here .. 
 still need help :(

---

### Post by ukripper on 2008-06-24
> **KenTor said:**
> OP here .. 
 still need help :(

check BIOS for temperature and fan speeds if temp is high then it means cooling fan is not doing its job but if temp is normal then cooling fan is fine and so is ur gfx. genrally, this X1950pro has a big cooler(my one has artic cooler ) and stil makes a lot of noise but it keeps my temp levelled and that is important.

You should check in BIOS for your temp as I have no idea why mbmon dint work on ur machine.

---

### Post by KenTor on 2008-06-24
> **ukripper said:**
> check BIOS for temperature and fan speeds if temp is high then it means cooling fan is not doing its job but if temp is normal then cooling fan is fine and so is ur gfx. genrally, this X1950pro has a big cooler(my one has artic cooler ) and stil makes a lot of noise but it keeps my temp levelled and that is important.

You should check in BIOS for your temp as I have no idea why mbmon dint work on ur machine.


Dude, i dont care if my gfx is getting warm or not .. 
 i just want the driver fixed :s

---

### Post by ukripper on 2008-06-25
> **KenTor said:**
> Dude, i dont care if my gfx is getting warm or not .. 
 i just want the driver fixed :s

On launchpad you can report this as a bug and developers will include the fix if they considered this as a problem in next release or provide you with drivers workaround as i see no problem with the same card i have been using past 2 years on ubuntu.

Easy solution is to replace your cooler with zalman one or better fix do soundproofing of your case [http://reviews.cnet.com/4520-11319_7-5670307-1.html](http://reviews.cnet.com/4520-11319_7-5670307-1.html)

---

