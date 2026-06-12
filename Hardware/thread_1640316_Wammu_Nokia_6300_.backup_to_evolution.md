---
title: "Wammu Nokia 6300 *.backup to evolution"
date: 2010-12-07
forum: Hardware
---

### Post by matzza on 2010-12-07
Dear all (little hackers),

I do have a Nokia 6300 cellphone. And I already created a backup of my contacts with wammu-gui, which looks like similar to this:
.
.
.
[PhonePBK064]
Location = 064
Entry00Type = Name
Entry00Text = "SomeName"
Entry01Type = NumberGeneral
Entry01Text = "+0491234567"
.
.
.
There are no messages, calendar entries or Tasks or Notes. Because I don't want them to be there.
I just want to have the phone-No and name.
-----------------------------------------------
So now I do have a file where all my contacts are stored and I want to import them into evolution.
I tried to fix this via bash-Script and creating a vCard from this file so that it is possible to import them into evolution.
But it seems that "grep" or "sed" isn't able, to read from a file, which is binary, to read from output whith "cat".
For example:
cat /Path/to/my/backupfile.backup | grep -i Entry00Text

doesn't give me any results.

Any suggestion or experiences on that?
Are there other ways to import Wammu *.backups into evolution?


r.
    Mazza

Using: ubuntu 10.04
Power: "strongenoughtogetthisdone"
Perl -v 
v5.10.1

---

