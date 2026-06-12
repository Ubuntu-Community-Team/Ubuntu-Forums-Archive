---
title: "ksh escape completion"
date: 2008-07-16
forum: General Help
---

### Post by some_guy on 2008-07-16
I'm looking to set up escape filename completion in ksh.  At work on HP-UX <esc> <esc> will complete filenames but I'm having no luck setting that up on my Ubuntu laptop.  Any ideas?

I've already run set -o vi.  I can post my .kshrc if needed but there is nothing too crazy in there.  I'd really like to get my terminal at home set up to work like my terminals at work.

Any help would be greatly appreciated.  Thanks.

---

### Post by ilrudie on 2008-07-17
I don't think ksh is meant to work that way.  It sounds like a difference in the way HP has implemented it.  It does not work that way on Solaris, AIX or any version of Linux I have (atleast by default it doesn't).  The normal ksh completion sequences are <esc>+\ and <esc>+*
In Ubuntu's version of ksh <tab> also seems to work.

<esc><esc> should just put you in command/beep mode and then beep if your using vi as your editor.  Did you make some changes to ksh on your HP-UX boxes or is this the default behavior?

---

### Post by some_guy on 2008-07-17
I wasn't there when our Unix boxes were set up but I don't think there was any special treatment done to ksh.  It's not the end of the world.  Thanks for the reply.

---

### Post by ilrudie on 2008-07-17
Sorry.  I don't have any HP-UX instances so I'm not sure if this is default or not.  I can contact a friend who admins HP-UX and ask him.  Like I said the standards are <esc>+\ and <esc>+*
Give these a try.  If i find out something about how it works on HP-UX I will post it for you.

---

### Post by some_guy on 2008-07-17
<esc>+\ works in ubuntu but I'm used to <esc><esc> and would like to set that up if possible.  I'll ask around at work as well.  Normally I can figure stuff out in no time (with the help of google) but this problem has me stumped.

Do you know if there a shell that,  in vi editing mode,  will complete filenames with <esc><esc>?

---

### Post by ilrudie on 2008-07-17
bash (bourne again shell) and csh (c shell) are the two other shells that it might be.  Give them a try.  Also at work just ```
echo $SHELL
``` to determine your default shell.  Linux generally defaults to bash.  AIX to ksh.  Solaris to sh.  I have never worked with HP-UX.

---

### Post by some_guy on 2008-07-18
After some time with my pal Google,  I found that pdksh with the set -o vi-esccomplete option gives me what I'm after.  I'm going to consider this case closed.

Thanks for the replies guys.  Rock on.

---

