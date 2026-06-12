---
title: "Firefox Hijacked"
date: 2005-11-08
forum: General Help
---

### Post by JamesNorris on 2005-11-08
I don't know how it happened, but every time I load Firefox, I get [http://www.whatuseek.com/](http://www.whatuseek.com/) as my homepage, even though it's set to about:blank 

Also, I can't load any session data, either, as it opens with a single tab, even though sessionSaver should restore my previous session (and always did until this started happening...)

Anyone any idea how I can fix this??

---

### Post by mustang on 2005-11-08
That's pretty weird. Have you tried reinstalling firefox?

---

### Post by JamesNorris on 2005-11-08
Yeah, I tried that... No luck... 

The preferences window shows that about:blank is my homepage, too... So I've no idea where to look!!

---

### Post by jasay on 2005-11-08
How are you loading firefox?  I know some people were having homepage trouble  with firefox launched from a gdesklets starterbar a couple months ago.  Taking the %U out of the launcher helped them.  Don't know if that is at all related.  

You also might back up your bookmarks, etc. and then delete the /home/username/.mozilla folder so that all preferences are lost and it should rebuild new files.  Uninstalling without "completely removing" the software may leave configuration files on your drive so a simple reinstall won't necessarily fix preference related errors.

---

### Post by Samuel on 2005-11-08
i got the same problem a few weeks back, there was also files in my home dir that i didnt put there so i deleted them and things went back to normal, wish i could remember exactley what i did but the whole incident lasted no longer than 5 mins...

---

### Post by steve.horsley on 2005-11-08
[QUOTE=JamesNorris]I don't know how it happened, but every time I load Firefox, I get [http://www.whatuseek.com/](http://www.whatuseek.com/) as my homepage, even though it's set to about:blank 

Also, I can't load any session data, either, as it opens with a single tab, even though sessionSaver should restore my previous session (and always did until this started happening...)

Anyone any idea how I can fix this??[/QUOTE]

It's a good question, how are you launching Firefox. Try launching from the command line, just to be sure there's nothing wrong with the launcher. If it still does it, try renaming the folder ~/.mozilla/firefox to something else while forefox is not running - this is the directory where firefox keeps its personalised settings. This will let you know if it's a stored setting. If using nautilus to do this, you will have to enable showing hidden files and folders.

Steve

---

### Post by JamesNorris on 2005-11-08
[QUOTE=jasay]How are you loading firefox?  I know some people were having homepage trouble  with firefox launched from a gdesklets starterbar a couple months ago.  Taking the %U out of the launcher helped them.  Don't know if that is at all related.  
[/QUOTE]

Yeah, this is it... What does the %u do?? That's how ubuntu has it's own shortcut in the menu, though... Problem solved now, but I'd like to know what this %u was doing, and get to the root of this problem, anyway...

---

### Post by imagine on 2005-11-08
You can give Firefox an URL as first parameter, which it will then load. Eg *firefox ubuntu.com* starts firefox und loads [http://ubuntu.com](http://ubuntu.com) right away.

Now the %u in the shortcut is a variable, which means that the program can take an URL or a list of URLs as start parameters, just as Firefox does. When the program is started, the variable %u is substituted for whatever was passed by the calling application. If nothing was passed then of course it will be substituted for nothing.

However gDesklets doesn't parse that parameter but sends it as-is to Firefox. That means Firefox starts and tries to open the URL **%u**. If you ever tried to enter invalid URLs in the address bar, you know that Firefox does a Google "I'm feeling lucky" search on them by default.
And now guess what site turns up when you do an "I'm feeling lucky" search for **%u**. Right...

Your Firefox isn't affected by any adware. I don't even know of any adware which could affect Firefox on a Linux system. It's just a bug in gDesklets or merely expected behaviour.
And btw another "I'm feeling lucky search" search, this time on firefox+whatuseek would have given you the solution to your problem too : )

---

### Post by JamesNorris on 2005-11-08
[QUOTE=imagine]You can give Firefox an URL as first parameter, which it will then load. Eg *firefox ubuntu.com* starts firefox und loads [http://ubuntu.com](http://ubuntu.com) right away.

Now the %u in the shortcut is a variable, which means that the program can take an URL or a list of URLs as start parameters, just as Firefox does. When the program is started, the variable %u is substituted for whatever was passed by the calling application. If nothing was passed then of course it will be substituted for nothing.

However gDesklets doesn't parse that parameter but sends it as-is to Firefox. That means Firefox starts and tries to open the URL **%u**. If you ever tried to enter invalid URLs in the address bar, you know that Firefox does a Google "I'm feeling lucky" search on them by default.
And now guess what site turns up when you do an "I'm feeling lucky" search for **%u**. Right...

Your Firefox isn't affected by any adware. I don't even know of any adware which could affect Firefox on a Linux system. It's just a bug in gDesklets or merely expected behaviour.
And btw another "I'm feeling lucky search" search, this time on firefox+whatuseek would have given you the solution to your problem too : )[/QUOTE]


Why thankyou, I wasn't using gdesklets, though... I didn't realise you could pass something direct to firefox like that, I knew it worked in konquerer, but not firefox. I didn't really think it was a hijack, but couldnt' possibly think what else it could be... After living with Windows for so long, I found it is best to be paranoid... I guess old habits die hard..

---

### Post by jasay on 2005-11-08
Yay, thanks imagine.  I'm learning things left and right today.:)

---

