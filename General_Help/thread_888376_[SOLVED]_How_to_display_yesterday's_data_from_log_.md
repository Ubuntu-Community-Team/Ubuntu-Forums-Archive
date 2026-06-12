---
title: "[SOLVED] How to display yesterday's data from log file?"
date: 2008-08-13
forum: General Help
---

### Post by abcuser on 2008-08-13
Hi,
in Ubuntu 8.04 my log file looks like bellow (first 10 characters in each line is date then follows message):
```

2008-08-11 Info - no error
2008-08-12 Check messages
2008-08-13 Error in section A
2008-08-13 Warning see data in section X

```

I would like to get all todays data from log file? So I did the following:
```
gawk 'substr($1,1,10)==CURRENT_DATE {print $0}' CURRENT_DATE=`date '+%Y-%m-%d'` myfile.log
```
The above script works fine. But now I need to display yesterdays data. How to get yesterday's data? And how to get day before yesterday's data?
Thanks,
Abcuser

---

### Post by justleen on 2008-08-13
you can enter a string for the date command with the -d option
```

date +%Y%m%d -d "12 august 2008"

```
or, enter any pronounceble string as date

```

date +%Y%m%d -d yesterday
date +%Y%m%d -d "2 days ago"
date +%Y%m%d -d "last year"

```

---

