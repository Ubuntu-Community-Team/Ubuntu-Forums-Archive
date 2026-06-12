---
title: "Android connected to computer no longer shows contents"
date: 2017-04-20
forum: Hardware
---

### Post by raleigh3 on 2017-04-20
Previously when I connected a Galaxy S5 to my computer, it would show the directories.

Now it shows nothing ?

I want to copy music from my computer to my phone.

---

### Post by RobGoss on 2017-04-20
Have you checked your settings on your device to see if USB debugging is enabled?

---

### Post by raleigh3 on 2017-04-20
> **RobGoss said:**
> Have you checked your settings on your device to see if USB debugging is enabled?

I do not know how to do that.

I assume you mean my cell phone.

---

### Post by RobGoss on 2017-04-20
Yes your phone it's a Android device correct? go to the **settings **and look under **developer options,** it should be there make sure the **debugging **option is checked then try connecting your device to your machine

You might have to enable the developer options first, see here [http://www.valuewalk.com/2014/04/samsung-galaxy-s5-enable-usb-debugging-mode/](http://www.valuewalk.com/2014/04/samsung-galaxy-s5-enable-usb-debugging-mode/)

---

### Post by RobGoss on 2017-04-20
I'm assuming you're using Ubuntu correct?

---

### Post by raleigh3 on 2017-04-20
There is no Develop Options.

---

### Post by RobGoss on 2017-04-21
Look at the link I posted you have to enable it

---

### Post by slickymaster on 2017-04-21
Install the [gmtp package]("http://packages.ubuntu.com/search?keywords=gmtp"), and use it to connect to the phone```
sudo apt install gmtp
```

---

### Post by raleigh3 on 2017-04-22
> **RobGoss said:**
> Yes your phone it's a Android device correct? go to the **settings **and look under **developer options,** it should be there make sure the **debugging **option is checked then try connecting your device to your machine

You might have to enable the developer options first, see here [http://www.valuewalk.com/2014/04/samsung-galaxy-s5-enable-usb-debugging-mode/](http://www.valuewalk.com/2014/04/samsung-galaxy-s5-enable-usb-debugging-mode/)

I did so. It did not help.

> **slickymaster said:**
> Install the [gmtp package]("http://packages.ubuntu.com/search?keywords=gmtp"), and use it to connect to the phone```
sudo apt install gmtp
```

I get "Detect: Unable to open raw device"

---

### Post by slickymaster on 2017-04-24
> **raleigh3 said:**
> I get "Detect: Unable to open raw device"
Install the mtp-tools and mtpfs packages and aftewards reboot your system```
sudo apt-get install mtp-tools mtpfs
```

---

