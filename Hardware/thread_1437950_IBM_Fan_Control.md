---
title: "IBM Fan Control"
date: 2010-03-24
forum: Hardware
---

### Post by rsmitty on 2010-03-24
Hi everyone,

Just wanted to put up a quick note to say that I've written a little Python script to control the fan speed in Thinkpads. A friend of mine was having some serious trouble with his getting incredibly loud in class. I've basically taken the instructions from:
[http://www.thinkwiki.org/wiki/How_to_control_fan_speed]("http://www.thinkwiki.org/wiki/How_to_control_fan_speed")
and generated an easier to use script. 

Here's how it works:

-Like in the ThinkWiki article, it is necessary to add the line     into the options file. This can be done by opening Terminal, and saying:
      ```
cd /etc/modprobe.d && sudo nano options
```

-In here, you’ll type:
      ```
options thinkpad acpi fan control=1
```

-Then, just hit CTRL+X, hit Y to save, then hit ENTER.
Now, you’ll just ‘cd’ in terminal to the directory your Python script is in. Then, you’ll just type:
    ```
sudo ./<whatever you choose to name the file>.py
```

-You’ll be prompted to enter a number which corresponds to the options on the ThinkWiki. Your choices are: 0, 2, 4, 7, auto, disengaged.

-Hit enter, and that’s it! It should cat the /proc/acpi/ibm/fan for you so that you can see that the settings took effect.

-Note: Be careful not to leave the fan off too long, if at all. It’ll roast everything. I’d suggest just turning it down.

Here's the script, in hopes that it helps someone!

```
#rsmitty
#March 24, 2010
#IBM Fan Control Script
 
#!/usr/bin/python
 
import os
 
number = raw_input('Please enter desired fan speed:')
 
os.system('echo level ' + number + ' > /proc/acpi/ibm/fan')
print os.system('cat /proc/acpi/ibm/fan')
```

---

