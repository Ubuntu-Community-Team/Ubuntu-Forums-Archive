---
title: "US International keyboard layout with Windows-like accent behavior?"
date: 2007-06-17
forum: Hardware &amp; Laptops
---

### Post by Leftblank on 2007-06-17
While using various distributions of Linux I've always had one question; 'How can I get my Us International keyboard to work with accents like it does on Windows?’

I'll explain this a bit further; I'm using a Logitech UltraX keyboard (normal keyset) with a US International layout (which is common in the Netherlands). For instance, when typing "don't" I can simply follow up those keys and the system figures where to put the quote. As second example, when I follow another character that can actually hold an accent, such as the "a" the output will be an á.

On the contrary, I can only get one of these two behaviors on Linux as far as I've figured out; the US International layout does drop the quote when followed by any key, but not an accent with extra modifiers. 

The second option is the Us International (with dead keys) layout, this does put the accents on certain characters, but sadly it attempts to do so with every key, even the l and others that never have one will appear and other keys will turn dead and follow without output, such as the t, which is often used when I type in English.

Hopefully I've made my issue clear a bit; I'd love to get back to the behavior I'm used to in Windows, which is pretty much like the most efficient way when typing both Dutch and English, without having to change my typing habits with those 'modifier keys'.

My question still stands, is this currently possible, and how would it be done?

---

### Post by IntuitiveNipple on 2007-06-17
Go to System -> Preferences -> Keyboard, select the Layout Options tab, expand **Compose key position** and choose your preference (I use the left or right Win-key depending on if the PC has 1 or 2 WinKeys).

Now type as normal. When you want to type a letter with an accent press the Compose key, then the letter, then the accent. Gnome will put the two together for you.

For example, to get the ñ I press and release the left Win-key, press "n", and finally press shift + "#/~" key. To get á I press and release left Win-key, press "a", and then press the "'/@" key.

---

### Post by Leftblank on 2007-06-18
> **IntuitiveNipple said:**
> Go to System -> Preferences -> Keyboard, select the Layout Options tab, expand **Compose key position** and choose your preference (I use the left or right Win-key depending on if the PC has 1 or 2 WinKeys).

Now type as normal. When you want to type a letter with an accent press the Compose key, then the letter, then the accent. Gnome will put the two together for you.

For example, to get the ñ I press and release the left Win-key, press "n", and finally press shift + "#/~" key. To get á I press and release left Win-key, press "a", and then press the "'/@" key.

I know that is the common way to do it, but I don't want to use extra modifier keys as I'm not the only one using the computer - I'd really love to get my keyboard to work the same as it does in Windows, like I stated in my title. Thanks a lot of your reply nonetheless, but it's not exactly what I'm looking for.

---

### Post by vanadium on 2007-06-18
System - Preferences - keyboard - layout "U.S. English International (with death keys)". This works like the Windows US International keyboard. The "compose key" approach is an additional (typically Linux) way of creating foreign characters.

---

### Post by Leftblank on 2007-06-18
Thanks for your reply, but sadly it doesn work like it does on Windows; when I hit the ['] key in Windows and follow it by an [n], I&#314;l get the output 'n, while Linux outputs &#324; (or in the case of a [t], nothing at all), which isn't the behavior I'd like to see, and also the reason I created this topic. 

Other suggestions are surely welcome though - if there are any.

---

### Post by Arathorn on 2007-06-20
I'd like to see this too. I hate the behaviour of the international setting for US keyboards in Linux and some Windows installations that turn 'e into é, since I use ' much more then é. So I'd like to have the behaviour be Ctrl + ', e  to become é (like in MS Office).
For Firefox there's the Zombie Keys addon which does just that, but I want to use this when typing in OpenOffice.org and other applications as well.

---

### Post by Leftblank on 2007-06-20
> **Arathorn said:**
> I'd like to see this too. I hate the behaviour of the international setting for US keyboards in Linux and some Windows installations that turn 'e into é, since I use ' much more then é. So I'd like to have the behaviour be Ctrl + ', e  to become é (like in MS Office).
For Firefox there's the Zombie Keys addon which does just that, but I want to use this when typing in OpenOffice.org and other applications as well.

That's no problem, simply use the 'US' keyboard setting (not the international). What I want is the Windows behavior so 'e will be turned into é, but 't will simply become 't.

---

### Post by Arathorn on 2007-06-20
That doesn't work here. I assume Kubuntu is using the same keyboard presets as Ubuntu? I'm using Kubuntu but I don't see any reason why the behaviour should be any different.

---

### Post by Leo the Lion on 2008-01-12
When I look for U.S. International in Keyboard Layout I can't see it. Where can I install it from? 
Right now I'm using the Compose Key.

Thanks

---

### Post by haran_elessar on 2008-03-18
I found this old thread trying to learn how to type accents using Ubuntu. At the moment I'm using Gutsy and I followed the instructions given here by Vanadium. I changed my keyboard layout to US International (first you select the keyboard layout and then select the modifier) and everything is working great.

LeftBlank was having the problem that when he typed ' and followed it by any character the ' would put itself on top of everything. When he wanted to use the apostrophe as is usually done in English as in "don't" it wouldn't work since it would do what I said before.

I'm using OpenOffice and I'm not having any of these problems. When I want to use the apostrophe I just hit the key and then hit the space bar and the apostrophe will appear. That way I'm able to write accents in Spanish and the apostrophes in English.

I'm guessing the problem got fixed with Gutsy so if anyone is having this problem you know what to do. The only bad thing is that this seems to work only in OpenOffice. When writing online it doesn't seem to work since I'm not able to put the accents over the vowels as I do in OpenOffice.

Well...hope this helps :).

---

### Post by haran_elessar on 2008-03-18
ok I found out how to make it work :)

I activated the compose key function as Arathorn suggested. This way I use the compose key method he explained whenever I'm writing in the internet and I use the other (easier) method when I'm writing in OpenOffice.

hope this helps :)

---

### Post by sephiros9883 on 2008-04-24
on Hardy 8.04 -

Hello,

I'm really disappointed there is no other solution to this than re-learn how to type. I need to be able to write in both english and french and I can't just relearn how to make the ç, and how the ' behave (as described in OP, in Windows, typing "I'll", you just need to type all those characters whereas in Ubuntu I have to type "I'<space>ll" or it will output "I&#314;l". Doing a ç in windows is " 'c"....)

doing "<alt>,c" is not an option when you are so used to one way to do it. I know Ubuntu is trying to be the most easy for windows switching users. But not be able to find the same keyboard behavior is a big big problem and that&#347; (<-- lol this exactly what happens with the current US international of Ubuntu...it would have displayed that's in windows) what prevents me to switch permanently.

---

### Post by Delenir on 2008-05-10
This was helpful! I wanted to click for a thanks to IntuitiveNipple's first post (which worked wonders for mé!) but the option seems to be gone since it's archive. :)

---

