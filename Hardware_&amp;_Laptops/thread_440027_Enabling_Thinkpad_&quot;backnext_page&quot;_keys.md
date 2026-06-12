---
title: "Enabling Thinkpad &quot;back/next page&quot; keys?"
date: 2007-05-11
forum: Hardware &amp; Laptops
---

### Post by Brian Kendig on 2007-05-11
My Thinkpad T40 has special keys above the left- and right-arrows which, under Windows, will go back or forward a page in a web browser. These keys don't have any effect in Ubuntu. I'd like to enable the keys in Ubuntu to work with Firefox and the file manager and any other applications that can use them.

I searched for instructions and found a lot of information which tells me how to use xmodmap to enable the keys and how to go in to the Firefox jar file and edit some lines to recognize the keys. But the information I found was dated from a few years ago, and I'm hoping that since then, someone's come up with a nicer way to enable the keys...

Is there any simple way to enable them? Is there a package I can install, for example?

---

### Post by integra_dc2 on 2007-06-03
i would like to know about this for my Thinkpad T43 as well.

can anyone help ?
thanks.

---

### Post by BeardlessForeigner on 2007-06-06
I just managed to get this working on my t43p, and even though it involves the method you stated I am happy because I didn't have to install new software and it also lets me use FN and Access IBM as normal shortcut buttons in Beryl and System/Preferences/Keyboard Shortcuts whereas before these keys were not recognized.

I will list what I did, although I just pieced it together from three other sites maybe it will help).

1st, read [http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work#xmodmap_configuration]("http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work#xmodmap_configuration") and type in the terminal:
```
gedit ~/.Xmodmap
```

and to make .Xmodmap and add (for forward/backward fuctionality and FN and Access IBM, nothing else was bothering me) 
```
keycode 159 = XF86LaunchA
keycode 234 = F19
keycode 233 = F20
keycode	227 = F35
```

Then after reading this [http://ubuntuguide.org/wiki/Ubuntu:Feisty#In_X_Windows]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#In_X_Windows") I ran in the terminal:
```
cp /etc/X11/xinit/xinitrc ~/.xinitrc
gedit ~/.xinitrc
```

and made the first line: 
```
xmodmap ~/.Xmodmap
```

After restarting X session with Ctrl-Alt-Backspace I selected the .Xmodmap file at startup. This has the keys read correctly and you should be able to use them as short cuts in beryl etc. For Firefox I had to edit /usr/lib/firefox/chrome/browser/content/browser/browser.xul by adding
```

<key id="goBackKb" keycode="VK_F19" command="Browser:Back" />
<key id="goForwardKb" keycode="VK_F20" command="Browser:Forward" />
```
to the <keyset id="mainKeyset">  section of the file. (see [http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work#Firefox]("http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work#Firefox")
restarted firefox, and everything was nice.

---

### Post by djennewe on 2007-09-20
BeardlessForeigner: I just tried this on a T42, and it worked like a charm.  Thanks for the tip!

---

### Post by thethendi on 2007-12-13
Likewise on a T43.  Thanks.

---

### Post by beetlejelly on 2008-04-27
hmmm ... this isn't working for me. It looks like the Xmodmap is working because when I run "xev" and press the back button I get ...
"keycode 234 (keysym 0xffd0, F19)," 
and foreward I get...
"keycode 233 (keysym 0xffd1, F20),"
I also added
```
<key id="goBackKb" keycode="VK_F19" command="Browser:Back" />
<key id="goForwardKb" keycode="VK_F20" command="Browser:Forward" />
```to the browser.xul file.
I'm using a T61.

---

### Post by franksxf on 2008-06-14
> **beetlejelly said:**
> hmmm ... this isn't working for me. It looks like the Xmodmap is working because when I run "xev" and press the back button I get ...
"keycode 234 (keysym 0xffd0, F19)," 
and foreward I get...
"keycode 233 (keysym 0xffd1, F20),"
I also added
```
<key id="goBackKb" keycode="VK_F19" command="Browser:Back" />
<key id="goForwardKb" keycode="VK_F20" command="Browser:Forward" />
```to the browser.xul file.
I'm using a T61.
A stupid question:
I just installed Ubuntu on my 2003 T40 and the Firefox version is 3.0, but how come I could not find this file? The chrome folder doesn't exist at all

---

### Post by samtihen on 2008-07-18
> **beetlejelly said:**
> hmmm ... this isn't working for me. It looks like the Xmodmap is working because when I run "xev" and press the back button I get ...
"keycode 234 (keysym 0xffd0, F19)," 
and foreward I get...
"keycode 233 (keysym 0xffd1, F20),"
I also added
```
<key id="goBackKb" keycode="VK_F19" command="Browser:Back" />
<key id="goForwardKb" keycode="VK_F20" command="Browser:Forward" />
```to the browser.xul file.
I'm using a T61.

Well, I'm using a T61 running 8.04.1.

For me, the solution was to use:

```

keycode 234 = XF86Back
keycode 233 = XF86Forward

```

instead of the F19 and F20.

Also, Firefox 3.0 doesn't require any additional configuration this way.

---

