---
title: "Brother printer only prints test page."
date: 2018-10-22
forum: Hardware
---

### Post by automate-stuff on 2018-10-22
The printer prints the test page...but when trying to print a non-test page the led on the printer blinks and Ubuntu gives me the message "Print completed" but no printing happens...


Can someone help ?

---

### Post by automate-stuff on 2018-10-22
[COLOR=#242729][FONT=Arial][CENTER][FONT=inherit]
[COLOR=#6A737C][FONT=inherit]0[/FONT][/COLOR]down voteaccept[/FONT][/CENTER]
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][FONT=inherit]I managed to fix this by removing the driver and then:[/FONT]
[FONT=inherit]apt-get purge cups
apt-get install cups[/FONT]
[FONT=inherit]and then reinstalling the driver as instructed here :[/FONT]

[/FONT][/COLOR]

[COLOR=#242729][FONT=Arial][CENTER][FONT=inherit][COLOR=#6A737C][FONT=inherit]0[/FONT][/COLOR]down voteaccept[/FONT][/CENTER]
[/FONT][/COLOR]
[COLOR=#242729][FONT=inherit]I managed to fix this by removing the driver and then:[/FONT][/COLOR]
[COLOR=#242729][FONT=inherit]apt-get purge cups
apt-get install cups[/FONT][/COLOR]
[FONT=inherit][COLOR=#242729]and then reinstalling the driver as instructed here :[/COLOR][/FONT]

[FONT=Arial, Helvetica Neue, Helvetica, sans-serif][COLOR=#242729]https://askubuntu.com/questions/966106/any-way-to-get-a-brother-hl-l2320d-to-work-with-current-ubuntu[/COLOR][/FONT]

---

### Post by ajayprajapati1995 on 2019-09-18
Have you tested online by using tool like [print test page]("https://colorprintertestpage.com/")? try it once you will get the solution.

---

