---
title: "update problem"
date: 2013-06-29
forum: Hardware
---

### Post by ashok72 on 2013-06-29
While running update manager the following error occured
E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_atareao_atareao_ubuntu_dists_quantal_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.

---

### Post by papibe on 2013-06-29
Hi ashok72. Welcome to the forum ):P

Could you open a terminal and post the result of this command?
```
find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
```
Regards.

---

### Post by ashok72 on 2013-06-29
@papibe Thank you, but Just now I have solved the problem with the following commands in terminal.
   
[LIST=1]
[*]
[COLOR=#000080][COLOR=#000000][SIZE=3]sudo rm /var/lib/apt/lists/* -vf[/SIZE][/COLOR][/COLOR]
[*][COLOR=#000080][COLOR=#000000]sudo 	apt-get update[/COLOR][/COLOR]

[*][COLOR=#000080][COLOR=#000000]sudo 	apt-get upgrade

Thank you once again for spending your valuable time to solve my problem.
[/COLOR][/COLOR]

[/LIST]

---

### Post by ashok72 on 2013-06-29
@papibe Thank you, but Just now I have solved the problem with the following commands in terminal.
   
[LIST=1]
[*][COLOR=#000080][COLOR=#000000][SIZE=3]sudo rm /var/lib/apt/lists/* -vf[/SIZE][/COLOR][/COLOR] 
[*][COLOR=#000080][COLOR=#000000]sudo     apt-get update[/COLOR][/COLOR] 
[*][COLOR=#000080][COLOR=#000000]sudo     apt-get upgrade

Thank you once again for spending your valuable time to solve my problem.
[/COLOR][/COLOR] 
[/LIST]

---

