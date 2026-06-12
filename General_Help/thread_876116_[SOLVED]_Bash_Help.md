---
title: "[SOLVED] Bash Help"
date: 2008-07-31
forum: General Help
---

### Post by MasterXandrex on 2008-07-31
All,

I'm trying to write a script that will automatically hotcopy some files and gzip them. However, I'm running into problems when it comes to some string manipulation. I'm looking into SED right now, but I find it confusing. I need to take the line:

```
r6654 | edw011 | 2008-07-30 15:50:54 -0400 (Wed, 30 Jul 2008) | 1 line
```

and extract the r6654 portion, however I can't limit the number of character as it will at some point be 6 characters long and I don't think that is good practice. 

Any help would be appreciated.

Xan

---

### Post by geirha on 2008-07-31
Either cut or awk should do the job:
```
echo 'r6654 | edw011 | 2008-07-30 15:50:54 -0400 (Wed, 30 Jul 2008) | 1 line' | cut -d'|' -f1
echo 'r6654 | edw011 | 2008-07-30 15:50:54 -0400 (Wed, 30 Jul 2008) | 1 line' | awk -F'|' '{print $1}'
```

You can do it with sed too, but cut and awk are the easier choices
```
echo 'r6654 | edw011 | 2008-07-30 15:50:54 -0400 (Wed, 30 Jul 2008) | 1 line' | sed 's/^\([^|]\+\).*$/\1/'
```

---

### Post by MasterXandrex on 2008-07-31
Thanks Geirha, I didn't know about cut.


Xan

---

### Post by decoherence on 2008-07-31
> **MasterXandrex said:**
> All,

I'm trying to write a script that will automatically hotcopy some files and gzip them. However, I'm running into problems when it comes to some string manipulation. I'm looking into SED right now, but I find it confusing. I need to take the line:

```
r6654 | edw011 | 2008-07-30 15:50:54 -0400 (Wed, 30 Jul 2008) | 1 line
```

and extract the r6654 portion, however I can't limit the number of character as it will at some point be 6 characters long and I don't think that is good practice. 

Any help would be appreciated.

Xan

The command you want is

```
awk '{print $1}'
```

for instance 
```

echo "r6654 | edw011 | 2008-07-30 15:50:54 -0400 (Wed, 30 Jul 2008) | 1 line" | awk '{print $1}'
```

$1 refers to the first field, as delimited by whitespace

actually, geirha's command is better if "|" is what you use as a deliminator

---

