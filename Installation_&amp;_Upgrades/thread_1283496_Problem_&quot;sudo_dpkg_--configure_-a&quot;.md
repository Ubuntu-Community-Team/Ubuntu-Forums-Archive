---
title: "Problem &quot;sudo dpkg --configure -a&quot;"
date: 2009-10-05
forum: Installation &amp; Upgrades
---

### Post by tubakid4327 on 2009-10-05
I am trying to update my OS using the updater.  I am getting an error saying I need to run the above command.  Whenever I run the ">>sudo dpkg --configure -a" as prompted by the updater I get another error:

dpkg: parse error, in file `/var/lib/dpkg/updates/0135' near line 1:
 newline in field name `#padding'

I am running Ubuntu 9.04 in a VM with Fusion on my MacBook, 1.83GHz, 2G.

I did encounter a problem where my laptop lost power (ran out of battery) in the middle of instaling Eclipse.

SSR

---

### Post by earthpigg on 2009-10-05
hi,

can you post the output of this, please:
```

cat /var/lib/dpkg/updates/0135
```

please put the output in code tags, 

```
like this
```

and not quote tags

> not like this

:D

---

### Post by arrange on 2009-10-05
Also the output of ```
ls -l /var/lib/dpkg/updates
df . -h
```

---

### Post by tubakid4327 on 2009-10-05
ran first command and got this

```
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding
#padding

```

---

### Post by tubakid4327 on 2009-10-05
Second two commands.  Output from both.

Thanks for the quick reply.

```

russelss193@ubuntu:~$ ls -l /var/lib/dpkg/updates
total 556
-rw-r--r-- 1 root root  118 2009-10-04 18:13 0000
-rw-r--r-- 1 root root  992 2009-10-04 18:14 0001
-rw-r--r-- 1 root root  985 2009-10-04 18:14 0002
-rw-r--r-- 1 root root  117 2009-10-04 18:14 0003
-rw-r--r-- 1 root root  894 2009-10-04 18:14 0004
-rw-r--r-- 1 root root  887 2009-10-04 18:14 0005
-rw-r--r-- 1 root root  116 2009-10-04 18:14 0006
-rw-r--r-- 1 root root 1095 2009-10-04 18:14 0007
-rw-r--r-- 1 root root 1088 2009-10-04 18:14 0008
-rw-r--r-- 1 root root  117 2009-10-04 18:14 0009
-rw-r--r-- 1 root root 1195 2009-10-04 18:14 0010
-rw-r--r-- 1 root root  142 2009-10-04 18:14 0011
-rw-r--r-- 1 root root 1036 2009-10-04 18:14 0012
-rw-r--r-- 1 root root 1029 2009-10-04 18:14 0013
-rw-r--r-- 1 root root  119 2009-10-04 18:14 0014
-rw-r--r-- 1 root root  899 2009-10-04 18:14 0015
-rw-r--r-- 1 root root  892 2009-10-04 18:14 0016
-rw-r--r-- 1 root root  125 2009-10-04 18:14 0017
-rw-r--r-- 1 root root  862 2009-10-04 18:14 0018
-rw-r--r-- 1 root root  855 2009-10-04 18:14 0019
-rw-r--r-- 1 root root  122 2009-10-04 18:14 0020
-rw-r--r-- 1 root root 1015 2009-10-04 18:14 0021
-rw-r--r-- 1 root root 1008 2009-10-04 18:14 0022
-rw-r--r-- 1 root root  110 2009-10-04 18:14 0023
-rw-r--r-- 1 root root  958 2009-10-04 18:14 0024
-rw-r--r-- 1 root root  951 2009-10-04 18:14 0025
-rw-r--r-- 1 root root  116 2009-10-04 18:14 0026
-rw-r--r-- 1 root root  882 2009-10-04 18:14 0027
-rw-r--r-- 1 root root  875 2009-10-04 18:14 0028
-rw-r--r-- 1 root root  124 2009-10-04 18:14 0029
-rw-r--r-- 1 root root 1094 2009-10-04 18:14 0030
-rw-r--r-- 1 root root 1087 2009-10-04 18:14 0031
-rw-r--r-- 1 root root  126 2009-10-04 18:14 0032
-rw-r--r-- 1 root root 1210 2009-10-04 18:14 0033
-rw-r--r-- 1 root root 1203 2009-10-04 18:14 0034
-rw-r--r-- 1 root root  127 2009-10-04 18:14 0035
-rw-r--r-- 1 root root  152 2009-10-04 18:14 0036
-rw-r--r-- 1 root root 1199 2009-10-04 18:14 0037
-rw-r--r-- 1 root root 1192 2009-10-04 18:14 0038
-rw-r--r-- 1 root root  123 2009-10-04 18:14 0039
-rw-r--r-- 1 root root  148 2009-10-04 18:14 0040
-rw-r--r-- 1 root root 1042 2009-10-04 18:14 0041
-rw-r--r-- 1 root root 1035 2009-10-04 18:14 0042
-rw-r--r-- 1 root root  134 2009-10-04 18:14 0043
-rw-r--r-- 1 root root 1583 2009-10-04 18:14 0044
-rw-r--r-- 1 root root 1576 2009-10-04 18:14 0045
-rw-r--r-- 1 root root  136 2009-10-04 18:14 0046
-rw-r--r-- 1 root root  652 2009-10-04 18:14 0047
-rw-r--r-- 1 root root  645 2009-10-04 18:14 0048
-rw-r--r-- 1 root root  122 2009-10-04 18:14 0049
-rw-r--r-- 1 root root  683 2009-10-04 18:14 0050
-rw-r--r-- 1 root root  676 2009-10-04 18:14 0051
-rw-r--r-- 1 root root  124 2009-10-04 18:14 0052
-rw-r--r-- 1 root root  775 2009-10-04 18:14 0053
-rw-r--r-- 1 root root  768 2009-10-04 18:14 0054
-rw-r--r-- 1 root root  135 2009-10-04 18:14 0055
-rw-r--r-- 1 root root  847 2009-10-04 18:14 0056
-rw-r--r-- 1 root root  840 2009-10-04 18:14 0057
-rw-r--r-- 1 root root  132 2009-10-04 18:14 0058
-rw-r--r-- 1 root root 1336 2009-10-04 18:14 0059
-rw-r--r-- 1 root root 1329 2009-10-04 18:14 0060
-rw-r--r-- 1 root root  126 2009-10-04 18:14 0061
-rw-r--r-- 1 root root  682 2009-10-04 18:14 0062
-rw-r--r-- 1 root root  675 2009-10-04 18:14 0063
-rw-r--r-- 1 root root  114 2009-10-04 18:14 0064
-rw-r--r-- 1 root root  139 2009-10-04 18:14 0065
-rw-r--r-- 1 root root  722 2009-10-04 18:14 0066
-rw-r--r-- 1 root root  715 2009-10-04 18:14 0067
-rw-r--r-- 1 root root  130 2009-10-04 18:14 0068
-rw-r--r-- 1 root root  759 2009-10-04 18:14 0069
-rw-r--r-- 1 root root  752 2009-10-04 18:14 0070
-rw-r--r-- 1 root root  141 2009-10-04 18:14 0071
-rw-r--r-- 1 root root 2591 2009-10-04 18:15 0072
-rw-r--r-- 1 root root 2584 2009-10-04 18:15 0073
-rw-r--r-- 1 root root  138 2009-10-04 18:15 0074
-rw-r--r-- 1 root root  902 2009-10-04 18:15 0075
-rw-r--r-- 1 root root  895 2009-10-04 18:15 0076
-rw-r--r-- 1 root root  125 2009-10-04 18:15 0077
-rw-r--r-- 1 root root  901 2009-10-04 18:15 0078
-rw-r--r-- 1 root root  894 2009-10-04 18:15 0079
-rw-r--r-- 1 root root  131 2009-10-04 18:15 0080
-rw-r--r-- 1 root root  993 2009-10-04 18:15 0081
-rw-r--r-- 1 root root  986 2009-10-04 18:15 0082
-rw-r--r-- 1 root root  133 2009-10-04 18:15 0083
-rw-r--r-- 1 root root  967 2009-10-04 18:15 0084
-rw-r--r-- 1 root root  960 2009-10-04 18:15 0085
-rw-r--r-- 1 root root  137 2009-10-04 18:15 0086
-rw-r--r-- 1 root root 1181 2009-10-04 18:15 0087
-rw-r--r-- 1 root root 1174 2009-10-04 18:15 0088
-rw-r--r-- 1 root root  124 2009-10-04 18:15 0089
-rw-r--r-- 1 root root 1112 2009-10-04 18:15 0090
-rw-r--r-- 1 root root 1105 2009-10-04 18:15 0091
-rw-r--r-- 1 root root  123 2009-10-04 18:15 0092
-rw-r--r-- 1 root root 1804 2009-10-04 18:15 0093
-rw-r--r-- 1 root root 1797 2009-10-04 18:15 0094
-rw-r--r-- 1 root root  112 2009-10-04 18:15 0095
-rw-r--r-- 1 root root  137 2009-10-04 18:15 0096
-rw-r--r-- 1 root root  857 2009-10-04 18:15 0097
-rw-r--r-- 1 root root  850 2009-10-04 18:15 0098
-rw-r--r-- 1 root root  116 2009-10-04 18:15 0099
-rw-r--r-- 1 root root  666 2009-10-04 18:15 0100
-rw-r--r-- 1 root root  659 2009-10-04 18:15 0101
-rw-r--r-- 1 root root  121 2009-10-04 18:15 0102
-rw-r--r-- 1 root root  967 2009-10-04 18:15 0103
-rw-r--r-- 1 root root  960 2009-10-04 18:15 0104
-rw-r--r-- 1 root root  125 2009-10-04 18:15 0105
-rw-r--r-- 1 root root  733 2009-10-04 18:16 0106
-rw-r--r-- 1 root root  726 2009-10-04 18:16 0107
-rw-r--r-- 1 root root  118 2009-10-04 18:16 0108
-rw-r--r-- 1 root root  612 2009-10-04 18:16 0109
-rw-r--r-- 1 root root  605 2009-10-04 18:16 0110
-rw-r--r-- 1 root root  136 2009-10-04 18:16 0111
-rw-r--r-- 1 root root  811 2009-10-04 18:16 0112
-rw-r--r-- 1 root root  804 2009-10-04 18:16 0113
-rw-r--r-- 1 root root  143 2009-10-04 18:16 0114
-rw-r--r-- 1 root root  944 2009-10-04 18:16 0115
-rw-r--r-- 1 root root  937 2009-10-04 18:16 0116
-rw-r--r-- 1 root root  117 2009-10-04 18:16 0117
-rw-r--r-- 1 root root  843 2009-10-04 18:16 0118
-rw-r--r-- 1 root root  836 2009-10-04 18:16 0119
-rw-r--r-- 1 root root  127 2009-10-04 18:16 0120
-rw-r--r-- 1 root root 1142 2009-10-04 18:16 0121
-rw-r--r-- 1 root root 1135 2009-10-04 18:16 0122
-rw-r--r-- 1 root root  123 2009-10-04 18:16 0123
-rw-r--r-- 1 root root  148 2009-10-04 18:16 0124
-rw-r--r-- 1 root root 1319 2009-10-04 18:16 0125
-rw-r--r-- 1 root root 1312 2009-10-04 18:16 0126
-rw-r--r-- 1 root root  119 2009-10-04 18:16 0127
-rw-r--r-- 1 root root  662 2009-10-04 18:16 0128
-rw-r--r-- 1 root root  655 2009-10-04 18:16 0129
-rw-r--r-- 1 root root  112 2009-10-04 18:16 0130
-rw-r--r-- 1 root root  137 2009-10-04 18:16 0131
-rw-r--r-- 1 root root 1224 2009-10-04 18:16 0132
-rw-r--r-- 1 root root 1217 2009-10-04 18:16 0133
-rw-r--r-- 1 root root  118 2009-10-04 18:16 0134
-rw-r--r-- 1 root root 1535 2009-10-04 18:16 0135
-rw-r--r-- 1 root root 1528 2009-10-04 18:16 0136
-rw-r--r-- 1 root root  120 2009-10-04 18:16 0137
-rw-r--r-- 1 root root 1056 2009-10-04 18:16 tmp.i
russelss193@ubuntu:~$ df . -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.4G  3.4G  5.6G  38% /
russelss193@ubuntu:~$
```

---

### Post by arrange on 2009-10-06
Just remove the problematic file or any other file that has the *#padding* gibberish in it. Then run the *sudo dpkg --configure -a* again.

---

