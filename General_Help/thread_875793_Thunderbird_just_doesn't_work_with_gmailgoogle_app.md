---
title: "Thunderbird just doesn't work with gmail/google apps."
date: 2008-07-31
forum: General Help
---

### Post by Avinash.Rao on 2008-07-31
Hi all,

I am sick of getting Thunderbird work with gmail for Pop/IMAP access. First i tried using POP and it never downloaded emails. So, i enabled IMAP and configured Thunderbird for the same and now i am getting Authentication error. This is happening for sometime now. 

I checked all the options, used the recommended settings frm gmail and yet it doesn't work.

Has anyone used Thunderbird  2.0.0.16 with gmail successfully!!

Thanks
Avinash

---

### Post by justleen on 2008-07-31
yea, im using it quite happily with POP forwarding of gmail.. 

in the help of gmail is an how-to setup thunderbird..

dont forget to turn on the pop option in your gmail account

---

### Post by Avinash.Rao on 2008-07-31
I have done all this!! 
:(

> **justleen said:**
> yea, im using it quite happily with POP forwarding of gmail.. 

in the help of gmail is an how-to setup thunderbird..

dont forget to turn on the pop option in your gmail account

---

### Post by Avinash.Rao on 2008-07-31
Here's another error... when i configured pop. Sending password didnot succeed. Mail Server pop.gmail.com responded Username and password not accepted.

POP is enabled in gmail!

---

### Post by jbowers on 2008-07-31
I've actually had some problems with one of my Gmail accounts that I have setup in Thunderbird (as IMAP) also. Everything is configured correctly and it works about 50% of the time with no problem.

However, about 2-3 times a day or more, the password manager appears for that account alone (I have 3 other non-gmail IMAP accounts configured in Thunderbird) and asks for my password again. At this point, I have to close out of Thunderbird and re-open it for it to take the password again. It will keep asking for the password if you type it in without closing out of Thunderbird.

I've tried removing and recreating the account a couple of times with no luck.

Anyone have any suggestions?

Thanks,

Justin

---

### Post by derrick81787 on 2008-07-31
My gmail account works beautifully in Thunderbird (POP3). Unfortunately, I'm at work right now, so I can't check my settings.  I'll try and check when I get home, though, so that I can post them on here.

- Derrick

---

### Post by jbowers on 2008-07-31
I've actually had some problems with one of my Gmail accounts that I have setup in Thunderbird (as IMAP) also. Everything is configured correctly and it works about 50% of the time with no problem.

However, about 2-3 times a day or more, the password manager appears for that account alone (I have 3 other non-gmail IMAP accounts configured in Thunderbird) and asks for my password again. At this point, I have to close out of Thunderbird and re-open it for it to take the password again. It will keep asking for the password if you type it in without closing out of Thunderbird.

I've tried removing and recreating the account a couple of times with no luck.

Anyone have any suggestions?

Thanks,

Justin

---

### Post by AlbertTatlocksCap on 2008-07-31
Ok I use Thunderbird for 3 of my POP3 email accounts including my Gmail account and it works absolutely fine 

I will try to post my settings later when I get home

---

### Post by Avinash.Rao on 2008-08-01
Hi all,

I found the solution for errors like "Invalid credentials" if u use IMAP and "Password not accepted by server" when you use POP.... its below

Attempts to download or send mail are failing. You might get a message
about how your credentials aren't valid, or your email client might
keep asking you for your password, over and over. You've already
checked that POP or IMAP is enabled in your Gmail Settings, your email
client is completely updated, and you're certain that your email
client's configuration matches the instructions in the Gmail Help
Center, down to the last screenshot. Still, you're stuck.

Luckily, you might be able to resolve this problem by clearing the
CAPTCHA. To clear the CAPTCHA, follow these steps:

1. Disable all mail clients you're using to read mail. (If you use one
at work and one at home, please disable both.)

2. From the computer or device on which your logins are failing, clear
the CAPTCHA.

--- For Gmail users, go here: [http://www.google.com/accounts/DisplayUnlockCaptcha](http://www.google.com/accounts/DisplayUnlockCaptcha)

--- For Google Apps users, use this address:
[https://www.google.com/a/](https://www.google.com/a/)[YOURDOMAIN.COM]/UnlockCaptcha

*Be sure to replace [YOURDOMAIN.COM] with your actual domain name.
Include everything after the "@" in your email address. For example,
if your email address is "yourname @ wildblue.net," you will put
"wildblue.net" into the URL: [https://www.google.com/a/wildblue.net/UnlockCaptcha](https://www.google.com/a/wildblue.net/UnlockCaptcha)

3. Enter your email username and password, and the letters in the
distorted picture.

4. Once you have successfully logged in, restart your mail client and
try to download your mail. 

Cheers
Avinash

---

### Post by ingeva on 2008-08-01
> **Avinash.Rao said:**
> Has anyone used Thunderbird  2.0.0.16 with gmail successfully!!

Works like a charm here, but I did have some trouble setting it up the first time.

Make sure you use SSL security protocol and ports 995 and 465 for send/receive.

POP address for gmail is pop.gmail.com, and SMTP address is smtp.gmail.com.

This should really work without any problem.

Just as an add-on: For other SMTP servers (than gmail) using anything but port 25 you may need to remove the "smtp" part from the server name.

---

### Post by Avinash.Rao on 2008-08-02
It worked after i unlocked my account in gmail.
[http://www.google.com/accounts/DisplayUnlockCaptcha](http://www.google.com/accounts/DisplayUnlockCaptcha)

---

### Post by snellcode on 2010-07-20
> **Avinash.Rao said:**
> Hi all,

I found the solution for errors like "Invalid credentials" if u use IMAP and "Password not accepted by server" when you use POP.... its below

Attempts to download or send mail are failing. You might get a message
about how your credentials aren't valid, or your email client might
keep asking you for your password, over and over. You've already
checked that POP or IMAP is enabled in your Gmail Settings, your email
client is completely updated, and you're certain that your email
client's configuration matches the instructions in the Gmail Help
Center, down to the last screenshot. Still, you're stuck.

Luckily, you might be able to resolve this problem by clearing the
CAPTCHA. To clear the CAPTCHA, follow these steps:

1. Disable all mail clients you're using to read mail. (If you use one
at work and one at home, please disable both.)

2. From the computer or device on which your logins are failing, clear
the CAPTCHA.

--- For Gmail users, go here: [http://www.google.com/accounts/DisplayUnlockCaptcha](http://www.google.com/accounts/DisplayUnlockCaptcha)

--- For Google Apps users, use this address:
[https://www.google.com/a/](https://www.google.com/a/)[YOURDOMAIN.COM]/UnlockCaptcha

*Be sure to replace [YOURDOMAIN.COM] with your actual domain name.
Include everything after the "@" in your email address. For example,
if your email address is "yourname @ wildblue.net," you will put
"wildblue.net" into the URL: [https://www.google.com/a/wildblue.net/UnlockCaptcha](https://www.google.com/a/wildblue.net/UnlockCaptcha)

3. Enter your email username and password, and the letters in the
distorted picture.

4. Once you have successfully logged in, restart your mail client and
try to download your mail. 

Cheers
Avinash


THANK YOU!!!!!!!

--- For Google Apps users, use this address:
[https://www.google.com/a/](https://www.google.com/a/)[YOURDOMAIN.COM]/UnlockCaptcha

it works, don't ask me why, but it does work.

---

