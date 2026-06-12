---
title: "Script to check temperatures / Taking  an integer value from a line in a file"
date: 2008-10-20
forum: General Help
---

### Post by slibuntu on 2008-10-20
Hi,

I'm trying to write a script to check the temperature values outputted by 'sensors'

I get the output, but I need to somehow get the integer value from a line like this
```
Core0 Temp:  +45.0°C
```

sed awk grep?? They all seem to operate on lines, how can I get this integer value out of this string to compare it to another integer??

Ripping my hair out, any ideas??

Thanks,
Shane

---

### Post by pedro_orange on 2008-10-20
What are you trying to do this in? Shell script?
Can't you save the line as a string/variable. Then apply a regular expression to return the text from the + onwards?

---

### Post by ilrudie on 2008-10-20
cat <your file> | grep "Core0 Temp:" | awk '{printf("%s",$3)}'
The grep part only matters if the file has more than one line in it.

---

### Post by slibuntu on 2008-10-20
You sir, are a genius! Thanks!

---

### Post by slibuntu on 2008-10-20
.

---

### Post by slibuntu on 2008-10-20
> **ilrudie said:**
> cat <your file> | grep "Core0 Temp:" | awk '{printf("%s",$3)}'
The grep part only matters if the file has more than one line in it.

How can I now operate on the value outputted from that command as an int?

---

### Post by alphaniner on 2008-10-20
If you want just the integer value, replace the '%s' (string) in the *printf* bit with '%i' (integer):  

```
cat file | grep "Core0 Temp:" | awk '{printf("%i",$3)}'
```

To get a floating point value, replace the '%s' with '%*x*.*y*f' where *x* is the number of digits before the decimal and *y* is the number after it.

```
cat file | grep "Core0 Temp:" | awk '{printf("%.1f",$3)}'
```

[printf info]("http://www.gnu.org/manual/gawk/html_node/Control-Letters.html#Control-Letters")

---

### Post by alphaniner on 2008-10-20
> **slibuntu said:**
> How can I now operate on the value outputted from that command as an int?

Don't know if this is the best way to do it, but I stored it as a variable in a script using

```
<variable>=`cat ./file | grep "Core0 Temp:" | awk '{printf("%i",$3)}'`
```

---

### Post by ilrudie on 2008-10-20
That should work.  As a side note variables in shell scripts are traditionally written in all CAPS letters but are not required to be.  To access a variable called CORETEMP you would use $CORETEMP as in ```
echo $CORETEMP
```

---

### Post by lswb on 2008-10-20
Here's one way

 echo Core0 Temp:  +45.0°C|grep -o "+[0-9]*" This will print +45, dropping off anything after the decimal point. If you think there will ever be below 0 temperatures reported, change it to 

grep -o "[-+][0-9.]*"


If you want to deal with the decimal point,

echo Core0 Temp:  +45.0°C|sed -n 's/.*\([-+][0-9]*\)\.\([0-9]\).*/\1 \2/p'

will print 45 followed by whitespace followed by 5. 

I would recommend testing with variety of expected and possible outputs from your "sensors" command to verify this works properly.

---

