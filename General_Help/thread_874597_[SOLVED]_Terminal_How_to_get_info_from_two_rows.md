---
title: "[SOLVED] Terminal: How to get info from two rows?"
date: 2008-07-30
forum: General Help
---

### Post by abcuser on 2008-07-30
Hi,
my log file looks like bellow sample. Two by two lines together form one info message.  I would like to get "Indicator name" for all "Alert state"=Alarm. In the sample bellow I would like to get "C"?
```
    
    Indicator Name = A
       Alert state = Normal

    Indicator Name = B
       Alert state = Normal

    Indicator Name = C
       Alert state = Alarm
```

By the way row position in file is constantly changing so I can write it for example to give me 8 row in file.

Any idea how to get names for all of the "Alarm" states?
Thanks,
Abcuser

---

### Post by iaculallad on 2008-07-30
You could use the grep command:

i.e: to get the "resolution mode" on dmesg log, i'll just do:

```
cat /var/log/dmesg | grep "resolution mode"
```

---

### Post by abcuser on 2008-07-30
iaculallad,
just grep will output: "Alert state" = Alarm, but I would not know which "Indicator name" has outputed alarm.
Thanks,
abcuser

---

### Post by abcuser on 2008-07-30
Hi,
after little twiking I have found out a solution:
```

 cat file | tr '\n' '~' | sed 's/~~/#/g' | tr '#' '\n' | tr -d '~' | gawk '$8=="Alarm" {print $4}'

```
Note: "file" is my file name.
Thanks,
Abcuser

---

