---
title: "MS Hotmail"
date: 2008-11-09
forum: General Help
---

### Post by nigel_salvador on 2008-11-09
I'm using Ubuntu Ubuntu 8.04. Hotmail does not allow me to compose a new email message or reply to an old message. Any help would be appreciated. Thanks.

---

### Post by _sAm_ on 2008-11-09
Take a look at this; [http://linux-watch.com/news/NS6023147333.html](http://linux-watch.com/news/NS6023147333.html)

MS want you to use Windows:-) 

I recommend Gmail, its free and better then Hotmail in any way - and works like a dream on all different OS.

---

### Post by scouser73 on 2008-11-09
Yes, unfortunately there is a problem with Hotmail but as _sAm_ says, Gmail works flawlessly on Ubuntu. There are many posts about Hotmail, I guess Microsoft have their reasons, it's shame they don't think of the users on other operating systems.

---

### Post by polybius on 2008-11-09
My wife uses hotmail and we had the same problem with Ubuntu 8.04, using Firefox 3.03.  She refuses to get a gmail account, so I had to figure out what was wrong.

The problem seems to be that Firefox on Ubuntu provides hotmail with some identification information that it doesn't like.  It throws up a message about your browser being out-of-date, which is nonsense considering that (in our case) it was Firefox 3.03.  You are given the option of continuing anyway, but if you do, you find you can only send blank emails.

Here is what worked for us.  Enter about:config into Firefox.  You will get a warning about voiding your warranty; click through it.  Then you will see a long list of Firefox options.  Scan down (or search) for general.useragent.vendor.  The default here is "Ubuntu".  Double click on it, change the value to "Firefox", click OK, then close and restart the browser.  Then try accessing hotmail.  It worked for us.

One thing, these setting in Firefox only work for one user on your Ubuntu system.  You need to change the "vendor" parameter on all users who want to access hotmail.

As near as I can tell, this is not Microsoft trying to force all users to switch to IE+Vista.  If it were, it would backfire, because it is just forcing users to switch to gmail.  It seems more likely to me that it is just incompetence in the programming of the hotmail interface.  This isn't the first time that hotmail has made trouble for Linux/Firefox users.

---

### Post by _sAm_ on 2008-11-09
Looking at the comments on digg tells me you are not alone; [http://digg.com/linux_unix/Microsoft_breaks_Hotmail_for_Linux_users](http://digg.com/linux_unix/Microsoft_breaks_Hotmail_for_Linux_users)
and this; [http://blogs.computerworld.com/hotmail_does_work_badly_with_linux](http://blogs.computerworld.com/hotmail_does_work_badly_with_linux)

One solution(if gmail is not an option) is to use Thunderbird + [http://webmail.mozdev.org/](http://webmail.mozdev.org/) to read/send mails via hotmail.

---

### Post by Emill on 2008-11-09
Another easy way is to install the plug-in User Agent Switcher and then use Firefox 3 for Windows.

---

### Post by thisgood on 2008-11-09
to polybius.

ref yr last

qte
Here is what worked for us. Enter about:config into Firefox. You will get a warning about voiding your warranty; click through it. Then you will see a long list of Firefox options. Scan down (or search) for general.useragent.vendor. The default here is "Ubuntu". Double click on it, change the value to "Firefox", click OK, then close and restart the browser. Then try accessing hotmail. It worked for us.
unqte

I would be extremely happy if u can explain exactly where i can find this 'about:config' u are mentioning.

I have the same problem as u have and also not so keen changing my email address eventhough it suchs that Hotmail isnt very compatiable with Linux.


Pleased to hear

Cheers,

---

### Post by PC_load_letter on 2008-11-09
Call me crazy, but I think if you read carefully thru the message from hotmail, you'll see a link that says "continue Windows live hotmail" or something like that. I have Ubuntu 8.04 and I use FF w/ hotmail read messages w/ no problems whatsoever. There is a problem w/ sending, javascript doesn't work! But w/ Opera, I can send/read messages w/ 0 problems. Opera also saves the password w/ the magic wand thing.

Still I have to agree gmail is light years better :D

---

### Post by CLomax on 2008-11-09
They had to make it unclear as to how to delete your account too.

[http://www.tech-recipes.com/rx/1149/close-out-or-cancel-your-hotmail-account/](http://www.tech-recipes.com/rx/1149/close-out-or-cancel-your-hotmail-account/)

---

### Post by thisgood on 2008-11-09
ahh found it somwhere else ( im new to linux )

enter about:config in address bar & change vendor from Ubuntu to Firefox.


anyway now it wont let me get it, says its the wrong password ...

---

### Post by nigel_salvador on 2008-11-09
Thank you everybody. I decided to go with Google Mail. It is the simplest solution. I was apprehensive to make the switch because I have had my Hotmail account for more than ten years. But if Microsoft cannot make a product that is compatible with the best operating systems on the market then that is their loss. After using Google mail for the past week I find it to be a far superior product to Hotmail. Oh Well Microsoft!!

Thanks

---

### Post by Yashiro on 2008-11-09
In the Firefox address bar, enter in:
```
about:config
```

open about:config in the address bar. Search the list for general.useragent.
Change whatever values you have set to the following:
```

general.useragent.extra.firefox  Firefox/3.0.3
general.useragent.vendor  Firefox
```

---

### Post by jflaker on 2008-11-09
Microsoft has another FAIL at compatibility

they broke it and I doubt you will see it fixed to work with anything else but MS products!

---

