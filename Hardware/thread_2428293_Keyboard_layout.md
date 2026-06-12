---
title: "Keyboard layout"
date: 2019-10-02
forum: Hardware
---

### Post by krobru94 on 2019-10-02
Hi,

I'm new to Linux 18 and I enjoy it ! But since yesterday I'm looking after solution to set my keyboard layout to Belgian but I didn't find anything, neither in settings, nor on the web.

So, after a few hours of searching I found this old file on the web who's gathering all the data that is important for people who lives in Belgium and uses Linux ([http://www.tldp.org/HOWTO/Belgian-HOWTO/configuration.html](http://www.tldp.org/HOWTO/Belgian-HOWTO/configuration.html)).

It's an old web site, made up in 2003, and they have a solution to set the keyboard to Belgium, they say to use "Xfree86" and set some lines like this :

```
Section "Keyboard"
	Protocol        "Standard"
	XkbRules        "xfree86"
	XkbModel        "pc101"
	XkbLayout       "be"
EndSection

```


But I also found that the file in etc/Default/keyboard contains some information written like this...


Do you think that I have to change this file manually to set my keyboard to Belgium ? Can you tell me more about "Xfree86" ? Isn't it too old ?


Thank you in advance ! I spent my all afternoon yesterday trying to find a solution...

Sorry for my spelling, I'm French...

---

### Post by #&amp;thj^% on 2019-10-02
Skip that link all together and look here: [https://linoxide.com/linux-how-to/configure-keyboard-ubuntu/](https://linoxide.com/linux-how-to/configure-keyboard-ubuntu/)

---

### Post by QIII on 2019-10-02
Hello!

Please use the default font, weight and color unless there is a compelling reason to highlight a particular part of your post for clarity or emphasis.

Also, please use code tags to contain text such as: commands; results of commands; and contents of files.  This preserves formatting and makes your posts easier to read.  

To use code tags, you may either:

1.  Click on the # button in the toolbars above the text entry box, place your cursor between the code tags that appear and then type or paste your text.  Alternatively, you may type or paste your text, highlight it and then click the #.

2.  Type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] following it.  The square brackets are required.

Finally, if English is not your first language, there is absolutely no need to apologize.  We are a world-wide community of people from every manner of culture and background. All that matters here is a common interest in supporting others with a common interest in Ubuntu.

Cheers!

---

### Post by krobru94 on 2019-10-03
Hi,

Yeah sorry for my syntax, it'll no more happen.

1fallen, I've check your link, tried to do what they said but it didn't work...

I've tried to change the keyboard file with :

```
 root@xx:/etc/default/# nano keyboard 
```

And after editing it and saving it like I wanted, after a quick restart nothing happen, the same layout, not the right one...

Do you have any idea ?

---

### Post by #&amp;thj^% on 2019-10-03
The correct syntax was right in that link via:
```
sudoedit /etc/default/keyboard
```

locate XKBLAYOUT= parameter and change it to your own preference e.g

XKBLAYOUT= 'us' <<English
Or: XKBLAYOUT= 'fr' <<French
You can configure the keyboard Language in one line. Once you have found your desired lang.
```
L='us' && sudo sed -i 's/XKBLAYOUT=\"\w*"/XKBLAYOUT=\"'$L'\"/g' /etc/default/keyboard
```
The above code sets it to US English
I'm not sure what option you want there seems to be a few choices for your Belgium choice.
If you tell what you want for keyboard language I'll give you a one-liner to set it with. :)

---

