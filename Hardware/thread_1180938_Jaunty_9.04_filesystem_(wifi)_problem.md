---
title: "Jaunty 9.04 filesystem (wifi?) problem"
date: 2009-06-07
forum: Hardware
---

### Post by tamashumi on 2009-06-07
Hi,

I have really strange problem.
Lets collect some facts:
[LIST=1]
[*]I'm running Ubuntu desktop on my laptop (Sony VAIO SZ650N)
[*]I was using Hardy Hadron 8.04 without such problems for almost a year
[*]After 
[*]After switched to jaunty my file-system getting damaged
[*]I've reinstalled it several times with partition format
[*]I checked hdd for bad-blocks - none
[*]I have vista on other partition which still works well
[*]I was trying ext3 and ext4
[*]After a week of re-installations the only longer stable period of system usage was without turning on wifi.
[*]running on lan cable no fsck problems detected at all even after 4 days of work.
[*] my system is up to date with apt-get update and upgrade
[*] my wifi adapter by lspci - Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
[/LIST]
Above facts allows me to consider that wifi makes system somehow unstable. Almost always after I turn it on strange things happens - starting from gnome applets corruption, by system freez, user directory damage, even ending up on whole system getting unbootable.
All of those become quite obvious after I run fsck which list really much different problems.


I would really appreciate if anyone could guide me at least to figure out what the hell going on.
I'm quite fluent with computer stuff but really don't know where to start this time.

Thanks,
Tom~

PS. other thing that really bothers me is why after first run of terminal console my hdd works as crazy and I have to wait more then 30sec until command prompt appear? (unless I hit ctrl+c) I checked on other console with top command that it's caused by find command. Why terminal runs find anyway o_O

---

