---
title: "cant log in as root..."
date: 2008-10-26
forum: General Help
---

### Post by keiran420 on 2008-10-26
ive installed ubuntu linux, and now i want t install xampp...

but i cant log in as root, i have tried....

su  <return>
my password

su root <return>
my password

su myusername <return>
root

su <return>
root


if i type in

su myusername <return>
mypassword

it just says use sudo command for admin stuff....

but this doesnt seem to work...

any advice?

am i doing it wrong?

---

### Post by cardinals_fan on 2008-10-26
Ubuntu uses sudo rather than su.  I don't like this, but it's forum policy not to explain how to enable the root account.  Have you tried "sudo aptitude install xampp"?

---

### Post by billgoldberg on 2008-10-26
> **keiran420 said:**
> ive installed ubuntu linux, and now i want t install xampp...

but i cant log in as root, i have tried....

su  <return>
my password

su root <return>
my password

su myusername <return>
root

su <return>
root


if i type in

su myusername <return>
mypassword

it just says use sudo command for admin stuff....

but this doesnt seem to work...

any advice?

am i doing it wrong?

Ubuntu doesn't come with a root account by default.

Just put sudo in front of the commands that require root access.

Installing xxxx would be done by using

sudo apt-install xxxx

If you want to enable the root account, google for it.

It's against forum policy to tell people how to do it.

If you can't figure it out by yourself, you shouldn't be using a root account.

--

There is a sudo timeout of 5 minutes.

Meaning that you only have to enter you password once in 5 minutes if you are in the terminal. 

You still have to put sudo in front of it though.

---

### Post by keiran420 on 2008-10-26
it says it cant find it, im meant to save it in the /opt file, but thats root only....

ive tried sudo chmod -R 777 /opt....

but doesnt do anything....

(id set it back after, but didnt get that far)


edited fr other reply...

"If you can't figure it out by yourself, you should be using a root account."

Well this is my pc, i am new to linuc, but even if i do 100% **** it all up, ill just reboot it all, no biggie, im only goint to learn from doing, and all my linux experiance is with suse....

can someone link a nice site for help, i have googled, but nothing nice and clear, just jargon or crap....

---

### Post by p_quarles on 2008-10-26
Moved to General Help.

You don't need to log into root to move files to /opt. You need to use sudo. If you would ask a question that is a bit more specific with respect to what you are trying to accomplish, I can guarantee you will get better answers.

---

### Post by billgoldberg on 2008-10-26
> **keiran420 said:**
> 

Well this is my pc, i am new to linuc, but even if i do 100% **** it all up, ill just reboot it all, no biggie, im only goint to learn from doing, and all my linux experiance is with suse....

can someone link a nice site for help, i have googled, but nothing nice and clear, just jargon or crap....

It's your pc right, and you can do with it what you want if you use the sudo command.

Just tell us what you want to do and you'll get the answer you want.

---

### Post by keiran420 on 2008-10-26
> **billgoldberg said:**
> It's your pc right, and you can do with it what you want if you use the sudo command.

Just tell us what you want to do and you'll get the answer you want.


i need to extract xampp.tar.gz to the root only folder of /opt

and install the muffa :)

sorry for my noobishness to ubuntu ^^

---

### Post by p_quarles on 2008-10-26
Try:
```
sudo mv xampp.tar.gz /opt/
sudo tar -zxf xampp.tar.gz
```

---

### Post by keiran420 on 2008-10-26
> **p_quarles said:**
> Try:
```
sudo mv xampp.tar.gz /opt/
sudo tar -zxf xampp.tar.gz
```

kool, installed in there now, but i still got a problem


[http://localhost](http://localhost)  =

Warning: file_get_contents(lang.tmp) [function.file-get-contents]: failed to open stream: Permission denied in /opt/lampp/htdocs/xampp/index.php on line 2

Warning: Cannot modify header information - headers already sent by (output started at /opt/lampp/htdocs/xampp/index.php:2) in /opt/lampp/htdocs/xampp/index.php on line 4


is this because the /opt file is still root only?

---

### Post by Spider44 on 2008-10-26
Use sudo instead of su when using Ubuntu.I had the same problem 2 days ago :P

---

