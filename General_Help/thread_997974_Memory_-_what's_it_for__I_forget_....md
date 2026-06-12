---
title: "Memory - what's it for?  I forget ..."
date: 2008-11-30
forum: General Help
---

### Post by JohnFH on 2008-11-30
I know about the commands free, vmstat, top, etc to find out how much memory is in use, but is there a tool or a way to find out actually what is in memory?  Is it possible to find out what's in application memory and what's in cache memory?

More specifically I'd like to know if things like pgp passphrases are stored in memory and/or swap.  Can *anything* from memory be swapped out or can certain things like pgp passphrases or other sensitive information be locked in memory so it can't be written to swap disk?  I read somewhere that it's possible for a pgp passphrase to be stored on disk, in swap and that surprised me to the point where I find it hard to believe.

That should test a few people I think.  :)

---

### Post by OrangeCrate on 2008-11-30
A basic understanding of how Linux uses memory is here:

[http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf)

There are different monitors to see what's using memory. In Gnome, look in your menu for System Monitor, or you can install Conky, which is my favorite. If you don't have it installed, just type "conky" into your terminal, and it'll tell you how to install.

Hope these tips help you, and I hope others will be along to comment on your other concerns...

---

### Post by JohnFH on 2008-12-03
Bump.  I thought this would generate more interest since it's not your usual 'I hate M$' topic or 'How do I log in to root?' or 'What window manager do you use?'.

I know it's not a stupid question, but maybe no-one knows the answer or knows where to find it ...

---

### Post by gTinker on 2008-12-03
[QUOTE=JohnFH]I thought this would generate more interest since it's not your usual 'I hate M$' topic or 'How do I log in to root?' or 'What window manager do you use?'.[/quote]

You also stated:

[QUOTE=JohnFH]That should test a few people I think. 
[/quote]

Perhaps people are here to help users with Ubuntu problems, rather than to be "tested".

[QUOTE=JohnFH]
I know it's not a stupid question, but maybe no-one knows the answer or knows where to find it ...[/QUOTE]

Yes, those are two possibilities, another, which you haven't mentioned, is that no one wants to do research for you. The context of your question suggests that you are not a noobie.

Attitude can make a huge difference in the quality of responses. Even if it is mistakenly interpreted.

---

### Post by JohnFH on 2008-12-03
Oh dear.  No I didn't put it up just as a test, but because I genuinely do want to know the answer.  I only said 'test people' as a light-hearted comment to spur people to help as I haven't found an explanation by the research I've already done.  The question has certainly tested me.  This forum is to help people and I asked a question, so I'm not sure why you have interpreted it any other way.

---

### Post by mkvnmtr on 2008-12-03
Well I think it is a pretty good question. I just don't have an answer. I have read that you can read ram memory for a short while. I am sure you could read swap memory because it is on the disk. I have no idea which apps might help do it. I would think forensic utilities would be the place to look. Might have to do it from a live disk or another machine. As for just seeing how much memory each app is using doesn't Htop give that information.

Folks seem kinda short tempered this afternoon. I guess it will pass.

---

### Post by sdennie on 2008-12-03
You can always use gdb to inspect what is living in a programs memory.  Try something like:

```

sleep 1000 &
gdb - $!
help data

```

(Assuming you wanted to debug the sleep command)

As for whether or not your PGP pass phrases can be stored in swap in "plaintext", the answer is almost surely "yes".  If that's really a worry for you, you can either disable swap or encrypt your swap.  This link looks good but I've not tried it: [http://ubuntumagnet.com/2007/11/creating-encrypted-swap-file-ubuntu-using-cryptsetup](http://ubuntumagnet.com/2007/11/creating-encrypted-swap-file-ubuntu-using-cryptsetup)

---

### Post by snova on 2008-12-03
I don't know how to get memory information on running processes (look in /proc though, there's a great deal if data there).

However, there is a way for a program to specify not to allow memory to be swapped out. I don't know how many programs use this, unfortunately, and assuming a security-sensitive program does this would not be wise.

I second what vor said, if you are concerned, encrypt your swap. I don't think it's difficult.

---

