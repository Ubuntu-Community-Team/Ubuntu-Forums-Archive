---
title: "sudo isn't working anymore"
date: 2009-09-23
forum: Installation &amp; Upgrades
---

### Post by zopanp on 2009-09-23
Hello evryone,
When I try to use the sudo command for anything it doesn't work anymore, it is the same for all gksu commands. I enabled the root account. when I try to use the sudo command this is what I get :
```
sudo: must be setuid root
``` 
Please help me.
thanks

---

### Post by tommcd on 2009-09-23
You should not enable the root account in Ubuntu. It is not recommended and is likely to cause problems, as you have discovered. If you want to use a root terminal in Ubuntu, use **sudo -i** like this:
[https://help.ubuntu.com/6.06/kubuntu/desktopguide/C/root-and-sudo.html](https://help.ubuntu.com/6.06/kubuntu/desktopguide/C/root-and-sudo.html)
See if this will fix the sudo problem:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by tgeer43 on 2009-09-23
I feel that there is more to this story. This usually only happens when the ownerships and/or permissions of certain key files or folders have been changed. Have you been experimenting with the 'chown' or 'chmod' commands? And what *exactly* do you mean when you say, "I enabled the root account."?

Depending on what has happened, there is hope for recovery but there is also the very real possibility that you've borked things beyond repair.

Try to remember *exactly* what you did just prior to receiving this error for the first time. You may be able to find the command(s) in question by looking through the .bash_history hidden file in your home directory.

tgeer

---

### Post by khelben1979 on 2009-09-23
When you went over to use root instead of sudo, did you follow [these instructions?]("http://www.sizlopedia.com/2008/04/16/how-to-login-to-ubuntu-as-root-user/")

As tommcd have written, it's recommended to stay with sudo instead.

---

### Post by zopanp on 2009-09-23
thanks for your answer and I think the problem might be with the command chown but I can't remenber what folders ownership where changed. could you tell me the most sensitive directories?
thanks

---

### Post by arrange on 2009-09-23
Have a look at
[http://ubuntuforums.org/showthread.php?t=219767](http://ubuntuforums.org/showthread.php?t=219767)
[http://mihirknows.blogspot.com/2008/06/sudo-must-be-setuid-root-solved-in.html](http://mihirknows.blogspot.com/2008/06/sudo-must-be-setuid-root-solved-in.html)

---

### Post by tgeer43 on 2009-09-23
> **zopanp said:**
> thanks for your answer and I think the problem might be with the command chown but I can't remenber what folders ownership where changed. could you tell me the most sensitive directories?
thanksWhen I correctly fingered the 'chown' command in my first response, I also explained that you can look through your command history by examining the .bash_history hidden file in your home directory or by simply typing 'history' in the console. You really need to know exactly what you did because trying to 'chown' things back in a willy-nilly fashion will more than likely make matters worse and is how you got in trouble in the first place. I'm not trying to be condescending - just trying to help you sort things out without exacerbating the situation.

tgeer

---

### Post by zopanp on 2009-09-29
sorryt for the late reply
the solution is:
```

chwon root:root /usr/bin/sudo
chmod 4755 /usr/bin/sudo

```
Thanks

---

