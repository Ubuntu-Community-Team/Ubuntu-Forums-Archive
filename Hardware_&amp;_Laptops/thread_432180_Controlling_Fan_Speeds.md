---
title: "Controlling Fan Speeds"
date: 2007-05-03
forum: Hardware &amp; Laptops
---

### Post by Sevan on 2007-05-03
I have a Dell Inspiron 1150 Laptop that has a well-documented history of overheating. In Windows there was a utility I could use to set my own fan speed parameters based on temperature. Since moving to Ubuntu I have not been able to do this. Any help in ways of controlling fan speeds in Ubuntu? Thanks.

---

### Post by NooneReally on 2007-05-03
```
sudo apt-get install i8kutils sensorsapplet
```

install sensorsapplet if you want to see temp/rpm on your tray.

if it was not added to /etc/modules when you installed i8kutils insert the following line at the end:

```
i8k force=1
```

In order for your fans to be controlled automagically you will need to run the i8k daemon when you start up. Go to System->preference->sessions->startup programs and add:

```
i8kmon -d -a
```

FINALLY...you will also need a config file called .i8kmon in your home directory, mine looks as such:

```
set config(0) {{- 0}  -1  30  -1  35}
set config(1) {{- 1}  25  42  30  50}
set config(2) {{- 2}  37  70  45  75}
set config(3) {{- 2}  60 128  65 128}
```

if you want to change the values you can change the thresholds to something that suits yourself. information can be found on the console by typing 'man i8kmon'

---

### Post by Sevan on 2007-05-04
Thanks a lot that worked fine. 

Anyone know of a GUI fan control program?

---

