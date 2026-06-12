---
title: "Samba needs restart"
date: 2008-10-17
forum: General Help
---

### Post by LeBurt on 2008-10-17
Hi all,

I'm having a bit of a nag with samba: every time I reboot Ubuntu (after an update), my shared folders are invisible from Windows stations but as soon as I restart samba manually with :

```
sudo /etc/init.d/samba restart
```

everything is fine and my shared folders become visible again from Windows.

Any idea why that is? How can I make it start right immediately after reboot?

Thanks!

---

### Post by shawnrgr on 2008-10-19
thats odd, you can try this and reboot

```
echo "gksudo /etc/init.d/samba restart" >> .xinitrc
```

you will have to enter your password in but it should be automatic. you could change gksudo to sudo and allow samba to run without password by editing your sudoers file, but i wouldn't do that with samba. if you want.. [http://blog.gunbladeiv.com/2008/05/edit-sudoers-for-no-pass-prompt.html](http://blog.gunbladeiv.com/2008/05/edit-sudoers-for-no-pass-prompt.html)

---

### Post by AreEK on 2008-10-19
Are you sure that Samba starts at boot at all? Check your /etc/rc.3 or /etc/rc.5 for files like Sxxsamba (where xx are a number).

---

