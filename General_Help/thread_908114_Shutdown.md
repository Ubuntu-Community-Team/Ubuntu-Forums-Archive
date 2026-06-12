---
title: "Shutdown"
date: 2008-09-02
forum: General Help
---

### Post by /////// on 2008-09-02
I would like my computer to shut down at a certain time using cron. I know I can just use the shutdown now or poweroff command, but both these commands needs me to run as root (ie type my sudo password) Is there anyway to get cron to shut down the computer at a certain time without it requiring you to input the password? (as I will not be there when the computer shuts down.)

---

### Post by jigsaws on 2008-09-02
So you can use root cron (i.e. sudo crontab -e).

---

### Post by /////// on 2008-09-02
O.o Heh should've read the whole cron documentation. Whoops xD

---

### Post by doug1212 on 2008-09-02
Hi,
This is what I did on my blackbox,

```
sudo crontab -e
```

Press the 'a' key to enter the text mode

Enter the following line (adjust time to suit):

```
30 22 * * * /sbin/shutdown -h now
```

Return to the command mode by pressing 'Esc' key

save the file by entering:

```
:w
```

Exit the editor by entering:

```
:q
```

To check the file enter:

```
crontab -l
```

The above example shuts the system down at 22:30 (10:30pm), adjust the values to suit your requirements.


Cheat sheet:)

[HTML]http://www.adminschoice.com/docs/crontab.htm[/HTML]


Doug.

---

### Post by Ryadt on 2008-09-02
```
sudo shutdown 12:00 -P
```
change the 12:00 to the time you want to shutdown.

---

