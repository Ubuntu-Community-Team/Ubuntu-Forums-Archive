---
title: "Problems getting wireless to work on a hp dv9000 notebook"
date: 2007-03-14
forum: Hardware &amp; Laptops
---

### Post by jrobinson5 on 2007-03-14
OK, so i'm trying to get Ubuntu to work on a Pavilion dv9000 notebook. Installation went supprisingly well, considering the horror stories of other users. However, wireless doesn't work out of the box, among other things. (not suprising, stupid broadcom...) So I tried to follow [these]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show") instructions to get it to work with ndiswrapper. The problem comes at this step:
```
jrobinson@laptop:~/bcm4311$ sudo ndiswrapper -a 14E4:4312 bcmwl5
couldn't create symlink for "14E4:4311:1363:103C.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4311:1364:103C.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4311:1365:103C.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4311.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4312:135F:103C.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4312:1360:103C.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4312:1361:103C.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4312:1362:103C.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4312.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4318:1355:103C.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4318:1356:103C.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4318:1357:103C.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4318.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4319:1358:103C.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4319:1359:103C.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4319:135A:103C.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4319.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4320:00E7:0E11.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4320:12F4:103C.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4320:12F8:103C.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4320:12FA:103C.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4320:12FB:103C.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4320.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4324:12F9:103C.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4324:12FC:103C.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4324.5.conf" -
installation may be incomplete
driver 'bcmwl5' is not installed (properly)!
jrobinson@laptop:~/bcm4311$

```
What can I do to correct this problem and get my wireless working?
James

---

### Post by teaker1s on 2007-03-14
okay well I'm not a big fan of editing config files so
```

sudo ndiswrapper -r bcmwl5
```

make sure all driver files are in same directory

```
sudo ndiswrapper -i bcmwl5.inf
```

do you have wired ethernet internet?

---

### Post by jrobinson5 on 2007-03-15
```
jrobinson@laptop:~/bcm4311$ sudo ndiswrapper -r bcmwl5
Password:
jrobinson@laptop:~/bcm4311$ sudo ndiswrapper -i bcmwl5.inf
installing bcmwl5 ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
jrobinson@laptop:~/bcm4311$ sudo ndiswrapper -a 14E4:4312 bcmwl5
couldn't create symlink for "14E4:4311:1363:103C.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4311:1364:103C.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4311:1365:103C.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4311.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4312:135F:103C.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4312:1360:103C.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4312:1361:103C.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4312:1362:103C.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4312.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4318:1355:103C.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4318:1356:103C.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4318:1357:103C.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4318.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4319:1358:103C.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4319:1359:103C.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4319:135A:103C.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4319.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4320:00E7:0E11.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4320:12F4:103C.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4320:12F8:103C.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4320:12FA:103C.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4320:12FB:103C.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4320.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4324:12F9:103C.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4324:12FC:103C.5.conf" -
installation may be incomplete
couldn't create symlink for "14E4:4324.5.conf" -
installation may be incomplete
driver 'bcmwl5' is not installed (properly)!
jrobinson@laptop:~/bcm4311$

```

Yes, I have both a wired and wireless connection available, but I prefer to use wireless. And I know my way around the terminal and have no problem editing config files.
James

---

### Post by teaker1s on 2007-03-17
i'm sorry I don't know that error, have you tried googling it or contacting ndiswraper project?

---

