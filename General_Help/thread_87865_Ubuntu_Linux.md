---
title: "Ubuntu Linux"
date: 2005-11-09
forum: General Help
---

### Post by alansii on 2005-11-09
[LEFT]:confused: Hello, i am Alan Sii Hee Kwong.I have some problem with my Ubuntu Linux 5.10I am a ADSL user. I format my old computer with Ubuntu and Kubuntu Linux 5.10 but I don know how to use ADSL with them?
Can some one teach me how? I am only a 12 years boy. So Computer Expert User please teach me.:confused: [/LEFT]

---

### Post by adwait on 2005-11-09
Hmm.......well if you have setup Kubuntu/Ubuntu, open up a terminal (Terminal in Ubuntu, Konsole in Kubuntu). Type
```
sudo pppoeconf
```
That should show you a blue screen.......now anser all the questions like your username, password etc. When its done, you are done. If you didn't select connect on boot, then you have to use to start your connection:
```
sudo pon dsl-provider
```
to stop it:
```
sudo poff
```

The password is your normal user password.

---

### Post by alansii on 2005-11-10
[LEFT]:D Thank you, adwait for you help!:KS [/LEFT]

---

