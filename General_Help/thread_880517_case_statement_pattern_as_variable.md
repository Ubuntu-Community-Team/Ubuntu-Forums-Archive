---
title: "case statement pattern as variable"
date: 2008-08-05
forum: General Help
---

### Post by danasp on 2008-08-05
Hi,

Have a problem where I try to use a variable holding a string as part of the pattern of a case statement. Like this:
##########
NAMES="apple|lemon"
case apple in 
		($NAMES)
		    echo "(MIGRATE)"
                    ;;
##########
It doesn't match the case that $NAMES includes apple.

But it works if I write it like this:
##########
case apple in 
		(apple|lemon)
		    echo "(MIGRATE)"
                    ;;
##########

Any idea how to get this working using the variable in a simple way?

Thanks!
//Daniel

---

### Post by H4rm0ny on 2008-08-05
You have a slight misunderstanding of how variable assignment works. When you type:
```

NAMES="apple|lemon"

```

You have lost the meaning of the [SIZE="4"]**|**[/SIZE] character - it's just another character now and **NAMES** is just a string and nothing more.  You'd have to re-parse it to get it back to being an actual expression meaning (apple OR lemon) and the **in** function wont do this for you. It just sees a string. Or possibly you thought that the **in** function was a string parsing function which it isn't - it is for checking elements of arrays. "apple" isn't in **NAMES**, only "apple|lemon" is.

Construct your **NAMES** variable as an actual array and the rest of your code will work. As follows:
```

NAMES=(apple lemon)
case apple in
($NAMES)
echo "(MIGRATE)";;
esac

```

---

### Post by danasp on 2008-08-05
Thanks for your quick reply Harmony.
It works better now but the case statement only seems to pick up the first entry in the array.

But if I put lemon first in the array, it fails.
```

NAMES=(lemon apple)
case apple in
($NAMES)
echo "(MIGRATE)";;
esac
```

Any suggestions? I can't seem to get this to work.

Reason for this question is that I have an issue with a init-script, xendomains, delivered with XEN. That script has the following declaration:
```
NAMES="$NAMES|$NM"
```
$NAMES is later used in a case statement like this:
```
case $name in
($NAMES)
# nothing
;;   
(*)    
echo -n "(skip)"          
continue      
;;      
esac

```

---

### Post by H4rm0ny on 2008-08-05
Okay, sorry about that. It's been quite a while since I did any Bash scripting and to be honest, I've never seen an array used in a case statement like that before and I just took your word for it that it could be done.

I don't know how to get it to work with a case statement. The code you quoted doesn't work for me, that's for sure. If you're just interested in getting this working, however, you could take a different approach as follows:

```

NAMES=(apple lemon)
foundit="0"
for i in ${NAMES[@]}
do
  if [ "$i" = "lemon" ]; then
    foundit="1"
  fi
done
if [ "$foundit" = "1" ]; then
  echo "(MIGRATE)"
fi

```

If you definitely want to use a case statement, then just refer to foundit in the statement, rather than the array. And obviously you can switch the hard-coded value of "lemon" in the first if statement to be a variable if you wish. Might want to break the loop early if foundit is true and your array list is particularly long.

Does that help? I'd be interested to know if you did get the array working in a case statement.

-H.

---

### Post by ibuclaw on 2008-08-05
> **H4rm0ny said:**
> 
```

NAMES=(apple lemon)
foundit="0"
for i in ${NAMES[@]}
do
  if [ "$i" = "lemon" ]; then
    foundit="1"
  fi
done
if [ "$foundit" = "1" ]; then
  echo "(MIGRATE)"
fi

```


You aren't far from the concept.
Case statements aren't that different from if, else, fi.
It is just case, match), esac instead.
```

#!/bin/bash
NAME=(potato apple lemon carrot)
for i in ${NAME[@]}
do
  case $i in
    apple)
      echo "$i is a fruit"
      ;;
    lemon)
      echo "$i is a fruit"
      ;;
    orange)
      echo "$i is a fruit"
      ;;
    banana)
      echo "$i is a fruit"
      ;;
    *)
      echo "$i isn't a fruit"
      ;;
  esac
done

```

A bit far fetched from the original example, but the idea is there.

Regards
Iain

---

### Post by danasp on 2008-08-06
Thanks a lot guys!
I realized that I didn't really need the case statement. The test script now looks like this:

```
#!/bin/bash
TEST="true";
N1="lemon"
N2="apple"
N3="other"
NAMES="$N1"
NAMES="$NAMES $N2"
NAMES="$NAMES $N3"
name="other" 
found="0"
if test $TEST = "true"; then
        for i in ${NAMES[@]}
        do
        if test $found = "0"; then
                if test $i = $name; then
                    echo "(MIGRATE)"
                    found=1
                fi
        fi
        done
        if test $found = "0"; then
                echo -n "(NOT MIGRATE)"
        fi
fi

```

Also managed to modify the "xendomains" script part of XEN so it can manage several running domains and not only one as when I started.

The original code looked like this:
```
for dom in $XENDOMAINS_AUTO/*; do
        rdname $dom
        if test -z $NAMES; then 
            NAMES=$NM; 
        else
            NAMES="$NAMES|$NM"
        fi
    done

```
Changed it to this:
```
for dom in $XENDOMAINS_AUTO/*; do       
        rdname $dom
        if test -z "$NAMES"; then      
            NAMES=$NM; 
        else
            NAMES="$NAMES $NM";            
        fi
    done

```
The code above is where the running domains are stored in NAMES.

And the code below is where I check for the match:

**OLD**
```
if test "$XENDOMAINS_AUTO_ONLY" = "true"; then
            case $name in
                ($NAMES)
                    # nothing
                    ;;
                (*)
                    echo -n "(skip)"
                    continue
                    ;;
            esac
        fi

```

**NEW**
```
found="0"
        if test "$XENDOMAINS_AUTO_ONLY" = "true"; then            
                for i in ${NAMES[@]}
                do
                if test $found="0"; then
                        if test $i = $name; then
                            found=1
                        fi
                fi
                done
                if test $found = "0"; then
                        echo -n "(skip)"
                        continue
                fi
        fi

```

Please comment if you see some silly mistake that could be improved.

Will post this to the xen-user ml and see what they say.
Do you believe the original code can be interpreted differently depending on Linux dist? So that it might work on CentOS of Fedora but not on Ubuntu? That was my first idea, as I can't see how this would go unnoticed if it applies to all dists.

Thanks again!
Now live migration works even with more than one VM running. Good improvement. ;)
//Daniel

---

### Post by H4rm0ny on 2008-08-06
**@tinivole:** Ah, thanks. Good to see an example of this. It occurred to me to take an approach like that, but the resulting process is actually different to danasp's original in that you could end up with multiple matches being executed. But I think your solution probably matches what he actually wanted. ;)

**@danasp:** Your new code looks good to me, though I'm not a Bash expert. You can build the **NAMES** array in one line in the first part of your code, but I presume you know that and have written it that way for readability / maintenance / own preference. It's not significant.

Anyway, I'm fairly sure that you're not going to experience differences in functionality between distributions. There's an older version of Bash out there somewhere (that doesn't even support arrays), but I'm pretty sure everything is going to be the same version anywhere you or I will run into it. If the original version you've changed does work, then I don't know how - it didn't for me.

Good work if this helps the Xen project, btw. And nice to find I could still (more or less) write a bash script after I don't want to think how many years. ;)

Regards,

Harmony.

---

