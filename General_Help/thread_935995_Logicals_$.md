---
title: "Logicals $"
date: 2008-10-02
forum: General Help
---

### Post by Rich78 on 2008-10-02
Hi, I'm currently working with RedHat9 at work, but I'm used to Ubuntu as my main server and desktop at home along with MacOSX.

I'm currently working a lot with what's termed as "logicals" where I can type $HOME for example or tst etc.  Without a cd in front and it will point me to a different location.

Can anyone confirm if this is pointing me to a different location on the same partition or a different one?  Does anyone know where these logicals are setup?

I've tried the lvmdiskscan -l which I found on the RedHat support site but firstly the command wasn't recognised and secondly the output on the RedHat site suggests the term logicals may not be the correct term?  This is what they're calling it at work.

I'm not sure but the logicals may also be user specific (ie setup for each system user).

Many thanks

---

### Post by justleen on 2008-10-02
the logicals are defined in different places.. .profile, .bashrc, /etc/profile

their not called logicals, they are called enviroment variables.
You can quite easily see what they are set to with the "env" command..
or,  with "echo $HOME"

"cd $HOME" should take you to the same place as a plain "cd"

---

### Post by Rich78 on 2008-10-02
Thankyou, that rings a bell.

I had earlier looked in /etc/bashrc and /etc/profile but couldn't find the logicals I am aware of.

where are .bashrc and .profile located?  or are they the same as the above?

If so is there anywhere else these enviroment variables can be setup?

---

### Post by Rich78 on 2008-10-02
I've now had our system explained to me by one of my colleagues.

Thanks again for the help.

---

