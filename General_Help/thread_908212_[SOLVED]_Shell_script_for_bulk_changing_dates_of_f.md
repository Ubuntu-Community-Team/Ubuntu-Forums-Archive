---
title: "[SOLVED] Shell script for bulk changing dates of files"
date: 2008-09-02
forum: General Help
---

### Post by muadnu on 2008-09-02
I took lots of pictures last weekend and my camera turned out to have a wrong date setting. I want to fix the dates of my pictures, basically I need to subtract 13 hours off the date/time of each file. I haven't found a file manager able to do this, so I guess the best way to go is to write a shell script and use the touch command to modify the dates. I guess it should be pretty simple to do, but due to my very basic knowledge of shell scripting and my being in hurry so I cannot start learning now, I could use some help... Thanks!

---

### Post by brian_p on 2008-09-02
> **muadnu said:**
> I took lots of pictures last weekend and my camera turned out to have a wrong date setting. I want to fix the dates of my pictures, basically I need to subtract 13 hours off the date/time of each file. I haven't found a file manager able to do this, so I guess the best way to go is to write a shell script and use the touch command to modify the dates. I guess it should be pretty simple to do, but due to my very basic knowledge of shell scripting and my being in hurry so I cannot start learning now, I could use some help... Thanks!

I think an example file name would help here.

---

### Post by muadnu on 2008-09-02
I'm not sure what you mean. I want to change the file's dates, not names. All the dates are shifted by 13 hours.

For example, suppose I have a file pic.jpg whose date is set to Sep. 1 2008, 01:19 AM. I'd need to change its date to Aug. 31 2008, 12:19 PM. This can be achieved by running (if I'm not mistaken)

```
touch -t 0808311219 pic.jpg
```

What I need is a script that goes over all files in a directory, retrieves the date of each file, subtracts 13 hours from it, and then modifies the date to the right one.

I hope it's clearer now.

---

### Post by kpkeerthi on 2008-09-02
Assuming ```
touch -t 0808311219 pic.jpg
``` works, an easy way to update the timstamp is by running
```
find /path/to/pictures/ -iname "*jpg" -exec touch -t 0808311219 '{}' ';'
```

---

### Post by muadnu on 2008-09-02
> **kpkeerthi said:**
> Assuming ```
touch -t 0808311219 pic.jpg
``` works, an easy way to update the timstamp is by running
```
find /path/to/pictures/ -iname "*jpg" -exec touch -t 0808311219 '{}' ';'
```

Ok, but that would change the date of every picture to 0808311219. What I need is to change the date of every file to its original date minus 13 hours, so I need to retrieve each date, compute the right date, and then modify it...

---

### Post by forger on 2008-09-02
Took half an hour by reading date and touch manuals:

**[COLOR="Red"]WARNING! Might break stuff![/COLOR]**
```
yourfolder=$HOME/pictures/badtimestamp
for i in $yourfolder/*; do a=`date -r "$i" +%s`; b=`expr $a - 43200`; c=`date -d "1970-01-01 $b sec" +"%Y%m%d%H%M.%S"`; touch -t $c $i; done
```

Change **yourfolder** to point to the folder where all the files you wish to subtract 13 hours from. (**Do NOT** add a slash "/" at the end)

FAQ:
- The idea is to convert the date/time in seconds since 1970-01-01 00:00:00 UTC
- Substract the amount of time in seconds (12 hours x 60 minutes x 60 seconds = 43200)
- Return it in a format that the touch command will recognize
Note: I noticed that it actually removes 14 hours if I subtract 13 hours, that's why I set it subtract 12 hours

Point of proof:
> 
$ ls -l test.jpg 
-rwx------ 1 user user 75186 2008-09-02 **[COLOR="Red"]17:51[/COLOR]** test.jpg
$ i=test.jpg; a=`date -r "$i" +%s`; b=`expr $a - 43200`; c=`date -d "1970-01-01 $b sec" +"%Y%m%d%H%M.%S"`; touch -t $c "$i";
$ ls -l test.jpg 
-rwx------ 1 user user 75186 2008-09-02 **[COLOR="Red"]04:51[/COLOR]** test.jpg


---

### Post by muadnu on 2008-09-02
Thanks, forger! It worked (almost) like a charm. Thanks again for the help and the half hour spent.

The only error in your posted code is in the first line: where it says "yourname=$HOME/..." it should say "z=$HOME/...". I guess the mistake came from trying to make the script more readable, but it had the unpleasant effect of trying to modify the date of everything in my root directory (nothing happened though since I wasn't running the script with sudo or as root).

Thanks again!

---

### Post by forger on 2008-09-02
heh, that's why I always use the "warning, might break stuff"
fixed the typo!

---

### Post by muadnu on 2008-09-04
Just in case some sees this and wants to use it, here goes a warning. When I initially tried the script it seemed to have worked, but later I realized that it didn't, the dates being set were not the correct ones. The mistake is just a small one, having to do with the time zone. When you convert dates to seconds using the date command, it computes the number of seconds since 1970-01-01 00:00:00 UTC, which is Greenwich time. When you convert the corrected number of seconds back to a date, it gives you the UTC time. My time zone is US Eastern Time, which is 5 hours behind London, and hence my "corrected" dates were off by 5 hours.

The fix is rather easy with forger's script in hand: simply add (or subtract) the time difference between your time zone and London's in seconds to the number of seconds used to shift the dates. In my case, I needed to subtract 18000 from the 43200 in forger's script.

I wonder whether that was the issue with forger's script using 13 instead of 12 hours. It might have to do with the 1 hour time difference (if I'm not mistaken) between Serbia and London.

---

