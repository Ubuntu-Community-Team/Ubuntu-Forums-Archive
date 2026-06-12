---
title: "Trying to &quot;debounce&quot; mouse which does untimely double clicks"
date: 2021-06-19
forum: Hardware
---

### Post by p4tr1x on 2021-06-19
Hello,
My USB mouse started to double click when I click only once.
I know it's a material problem, but I don't want to buy another mouse _again_ if it can be fixed by software.
I've read that the libinput library can handle this with "debounce".
So I installed it (on Xubuntu 20.04) but apparently it does not work automatically. I don't know how to configure this.
Any help please?

---

### Post by him610 on 2021-06-20
If you are using Xubuntu 20.04, you should be able to adjust the behavior of your mouse by going to Settings->Mouse and Touchpad, click on the Behavior tab. You might want to play around with the Double Click Time setting to see if that addresses your mouse issue. Mine is set relatively slow at 400 ms, but occasionally I get a double click because of a slow or lazy finger.

---

### Post by p4tr1x on 2021-06-23
The settings only set the maximum double-click delay. But I want to set the _minimum_ delay to prevent this bouncing problem.

---

### Post by sushi-addiction13 on 2021-12-06
It's about time *ubuntu added a proper debounce option  Is xubuntu using libinput?  [https://askubuntu.com/questions/1351909/lowering-mouse-debounce-time](https://askubuntu.com/questions/1351909/lowering-mouse-debounce-time)  get mouse name sudo libinput list-devices | grep Device  or  xinput list --name-only | hexdump -C  The hexdump is because some mice have a space at the end. e.g. "USB OPTICAL MOUSE "  cd /usr/share/libinput  create new file with  sudo touch local-overrides.quirks  Then edit local-overrides.quirks  [Mouse Name]  MatchName=Mouse Name  ModelBouncingKeys=20  that is 20ms  e.g.  [USB OPTICAL MOUSE ]  MatchName=USB OPTICAL MOUSE  ModelBouncingKeys=20

---

