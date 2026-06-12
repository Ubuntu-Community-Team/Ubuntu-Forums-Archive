---
title: "[SOLVED] Multiple Conditions for &amp;quot;if&amp;quot; statements in bash scripts"
date: 2008-11-29
forum: General Help
---

### Post by trumpeteersman on 2008-11-29
This is a question for the bash scriptwriters out there.

I can't get this check code to work right:

```

if [[ "$begin" != {1...254} || "$end" != {1...254} || "$begin" > "$end" ]];then
echo -e "Usage Error"
exit 2
fi

```

It is supposed to check if the variables $begin and $end are numbers 1 through 254 and that the $begin is smaller than $end. Else return an error.

However, the conditions always return true and never get to executing the main code, even when the check should pass.

I tried seperating each condition like this:
```

if [[ "$begin" != {1...254} ]] || [[ "$end" != {1...254} ]] || [[ "$begin" > "$end" ]]

```

I also tried with out quotes and with no double brackets.

What is the proper way to do this?

---

### Post by unutbu on 2008-11-29
How about this?
```
#!/bin/bash
begin=$1
end=$2
if [ "$begin" -lt 1 ] || [ "$begin" -gt 254 ] || [ "$end" -lt 1 ] || [ "$end" -gt 254 ] || [ "$begin" -gt "$end" ]; then
    echo -e "Usage Error"
    exit 2
fi

```

---

### Post by DGortze380 on 2008-11-29
> **trumpeteersman said:**
> This is a question for the bash scriptwriters out there.

I can't get this check code to work right:

```

if [[ "$begin" != {1...254} || "$end" != {1...254} || "$begin" > "$end" ]];then
echo -e "Usage Error"
exit 2
fi

```

It is supposed to check if the variables $begin and $end are numbers 1 through 254 and that the $begin is smaller than $end. Else return an error.


logic error.

you explained using the and ( && ) operator, but your code uses the or operator ( || )


the if statement you posted says:

if begin is not between 1 - 254 OR if end is not between 1 - 254 OR begin > end

---

### Post by trumpeteersman on 2008-11-29
Thanks for your response unutbu!  Your idea seems to be working. Here is the check so far:

```

#!/bin/bash
begin=$1
end=$2

if [[ "$begin" -lt 1 ]] || [[ "$begin" -gt 254 ]] || [[ "$end" -lt 1 ]] || [[ "$end" -gt 254 ]] || [[ "$begin" -gt "$end" ]] || [[ "$begin" = "!" ]] || [[ "$end" = "!" ]]; then
  echo -e "Usage Error\n"
  exit 2
fi



```

However, it still tries to run the code if I put weird characters in it, like "!".  As you can see, I put a detect for this, but it gives this error:
```

line 12: [[: !: syntax error: operand expected (error token is "!")

```

Is it possible to have the script catch these special characters and give the general error?

Is there a way I can protect the code from situations like that?

---

### Post by trumpeteersman on 2008-11-29
Regarding DGortze380:

I know it seems confusing the way I said it, sorry about that.

If $begin or $end are not numbers from 1-254, then return error.
If $begin is greater than $end, return error.

---

### Post by geirha on 2008-11-29
! is used for history expansion in bash, and is a bit awkward to escape. Hard quotes is the best way.
```

$ echo !foo
-bash: !foo: event not found
$ echo "!foo"
-bash: !foo: event not found
$ echo '!foo'
!foo
$ echo \!foo
!foo

```

Once it's stored in a variable though, it will no longer be expanded:
```

$ var='!foo'
$ echo $var "$var"
!foo !foo

```

So make sure you quote/escape the arguments to the script properly.

---

### Post by trumpeteersman on 2008-11-29
This is the best I can do so far.  The "!" in the script gives me a syntax error when I have a "!" as input AND outputs my Error Message.
I could list all possible special characters for $begin and $end, but that would be tedious and the script would look horrible.  Is there a better way?

"*" builtin still goes through, so does "&".

```

#!/bin/bash

begin="$1"
end="$2"
if [[ "$begin" -lt 1 ]] || [[ "$begin" -gt 254 ]] || [[ "$end" -lt 1 ]] || [[ "$end" -gt 254 ]] || [[ "$begin" -gt "$end" ]] || [[ "$begin" = "!" ]]; then
  echo -e "Usage Error\n"
  exit 2
fi

```

Thank you for your help.

---

### Post by unutbu on 2008-11-30
Perhaps try this:
```
#!/bin/bash

begin="$1"
end="$2"
echo begin "$begin"
echo end "$end"

re="[0-9]+"
if ! ( [[ "$begin" =~ ${re} ]] && [[ "$end" =~ ${re} ]] && [[ "$begin" -gt 0 ]] && [[ "$begin" -lt 255 ]] && [[ "$end" -gt 0 ]] && [[ "$end" -lt 255 ]] && [[ "$begin" -lt "$end" ]] ) ; then
    echo -e "Usage Error\n"
    exit 2
fi

```

---

### Post by trumpeteersman on 2008-11-30
Awesome! That works perfectly.  Thank you unutbu.  This handles everything that I can throw at it.  And it is easier to understand since it is not logically backwards anymore.  Yay for better scripting.

---

