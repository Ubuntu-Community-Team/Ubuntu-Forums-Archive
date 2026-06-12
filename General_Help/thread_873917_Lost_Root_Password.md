---
title: "Lost Root Password"
date: 2008-07-29
forum: General Help
---

### Post by dgeddes on 2008-07-29
I have forgotten my root password and need to install some new SW. Can anyone tell me how to recover my password.

Thanks,

---

### Post by NilsE on 2008-07-29
> **dgeddes said:**
> I have forgotten my root password and need to install some new SW. Can anyone tell me how to recover my password.

Thanks,In order to install software all you need is your regular login password. When Synaptic, update manager or apt-get asks for a password just enter your regular login password.

---

### Post by dgeddes on 2008-07-29
Thanks for your response but that is not my problem. I am trying to install RealPlayer11Gold which is not available with Synaptic. I need to su root to do it.

thanks,

---

### Post by snowpine on 2008-07-29
NilsE is correct, and if you are curious about the reason why: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You just need your normal user password, no need to log in as root to install software.

---

### Post by snowpine on 2008-07-29
(double post)

---

### Post by Titan8990 on 2008-07-29
I have been using Ubuntu for a while now and the only time I have ever had to do su is to navigate server directories that my user did not have read permissions for. It seems absolutely everything can be sudoed.

---

### Post by gjoellee on 2008-07-29
go to System->Administration->Users and Groups click on root and unlock. Then select root again and click on preferences, now set password by hand and click OK. You are done!

---

### Post by Hawk__0 on 2008-07-29
or you could jsut use your regular user account to change the password.
```
sudo passwd root
```
should do the trick.

---

### Post by Titan8990 on 2008-07-29
I believe that it is against the policy of the forums to tell him how to do that...

---

### Post by lukjad on 2008-07-29
[COLOR="#D900B3"]Don't forget that usually your regular password is setup as the root password. Try it and see if it works.[/COLOR]

---

### Post by snowpine on 2008-07-29
You certainly *could* do that, but do yourself a favor and learn how to use sudo. Believe me when I tell you you do not need to change your root password to install software. :)

---

### Post by lukjad on 2008-07-29
[COLOR="#D900B3"]True.[/COLOR]

---

### Post by snowpine on 2008-07-29
I think these discussions often get started when someone is reading "linux installation instructions" that are not specific to ubuntu. On a different flavor of linux that does not have sudo, "log in as root and do x, y, and z" may be perfectly valid instructions. Part of the learning curve of Ubuntu is learning what makes it special.

---

### Post by LowSky on 2008-07-29
how to install Realplayer 11
[http://www.associatedcontent.com/article/705055/how_to_install_realplayer_11_in_ubuntu.html](http://www.associatedcontent.com/article/705055/how_to_install_realplayer_11_in_ubuntu.html)

No need for root password access, Sudo will work!

---

### Post by ajgreeny on 2008-07-29
I'm not sure about RealPlayer 11Gold, but Realplayer 10 is available in the medibuntu repos, so go to [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) to learn how to enable them.  There are a lot of other very useful packages there for multimedia that you may find worth installing as well.

---

### Post by aysiu on 2008-07-29
There is no root password to lose, unless you've set one up.

In Ubuntu, you use your user password to authenticate to temporarily gain root privileges for particular tasks, and then only if you belong to the *admin* group.

If you've forgotten your *user* password, you can reset it by following these instructions:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

