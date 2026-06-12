---
title: "[SOLVED] Bash script: How to get script file name commands are executed from?"
date: 2008-08-08
forum: General Help
---

### Post by abcuser on 2008-08-08
Hi,
in Ubuntu 8.04 I have several bash scripts. I would like to write to log file script_file_name from witch command is executed from.

Sample:
--- script file: **1.sh** ---
echo **"1.sh**" >> mylog.log

--- script file: **2.sh** ---
echo "**2.sh**" >> mylog.log

Is there any command I could write:
echo "$get_name_of_this_scrip_file

Now if file get renamed I need to manually rename echo command in script file. I would like to avoid this renaming.

Regards,
Abcuser

---

### Post by Vixis on 2008-08-08
echo $0 >> mylog.log

---

### Post by Bachstelze on 2008-08-08
Use [font="Courier new"]basename[/font] and the special [font="Courier New"]$0[/font] variable:

```
firas@nobue ~ % cat test.sh
#!/bin/sh

echo "hello world!" >> `basename $0`.log
firas@nobue ~ % cat test.sh
#!/bin/sh

echo "hello world!" >> `basename $0`.log
firas@nobue ~ % ./test.sh
firas@nobue ~ % cat test.sh.log
hello world!
hello world!

```


*Edit : woops, I misunderstood the question :p thought you wanted each script to write to its own logfile. Well, [font="Courier New"]basename[/font] can still be useful, I guess.*

---

### Post by abcuser on 2008-08-08
Vixis, thanks that solves my problem.

I have found "special parameters" tutorial:
[http://www.gnu.org/software/bash/manual/html_node/Special-Parameters.html#Special-Parameters](http://www.gnu.org/software/bash/manual/html_node/Special-Parameters.html#Special-Parameters)

---

