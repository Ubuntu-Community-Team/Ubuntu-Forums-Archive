---
title: "wd 500 gb hard drive with read errors"
date: 2009-01-28
forum: Hardware
---

### Post by foilpan on 2009-01-28
i have a 500 gb secondary drive that caused me problems in the past, but i just tried reformatting and remounting it as a secondary. /dev/sda1 is boot, /dev/sdb1 is just one big partition for storage.

smartctl reports the following, but is this drive safe to keep in there, or would it be a good idea to rma it?

thanks for any input you might have.

```
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       90%       940         278815168
# 2  Extended offline    Completed: read failure       90%       940         278815168
# 3  Short offline       Completed: read failure       90%       940         278815168
# 4  Short offline       Completed: read failure       90%       886         278815168
# 5  Extended offline    Completed: read failure       90%       886         278815168
# 6  Extended offline    Completed: read failure       90%       866         278815168
# 7  Extended offline    Completed: read failure       90%       866         278815168
# 8  Extended offline    Completed: read failure       90%       866         278815168
# 9  Extended offline    Completed: read failure       90%       866         278815168
#10  Short offline       Completed: read failure       90%       866         278815168
#11  Short offline       Completed: read failure       90%       866         278815168

```

---

### Post by cariboo on 2009-01-28
It prorbably would be a good idea to run the WD diagnostic software on it, it will give you an error code that will help with the RMA.

Jim

---

### Post by foilpan on 2009-01-28
is that windows only? i'll take a look but don't have any windows boxes on hand to test.

---

