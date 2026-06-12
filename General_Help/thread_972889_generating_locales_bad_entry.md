---
title: "generating locales bad entry"
date: 2008-11-06
forum: General Help
---

### Post by antuanjoseff on 2008-11-06
hi all,

I have updated from 6.06 to 8.04. I'm not sure everything went ok because when trying to install some packages I get the following error:

error processing locales (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 locales

And I cann't remove locales.

I have also tried to reconfigure locales with:
sudo dpkg-reconfigure locales --force

but then again I get another error... 

Generating locales...
Error: Bad entry '"<U0061><U0062><U0072><U0069><U006C>";/ '
Error: Bad entry '"<U0061><U0067><U006F><U0073><U0074><U006F>";/ '
Error: Bad entry '"<U0064><U0069><U0063><U0069><U0065><U006D><U0062><U0072><U0065>" '
Error: Bad entry '"<U0066><U0065><U0062><U0072><U0065><U0072><U006F>";/ '
Error: Bad entry '"<U006A><U0075><U0065>";"<U0076><U0069><U0065>";/ '
Error: Bad entry '"<U006A><U0075><U0065><U0076><U0065><U0073>";/ '
Error: Bad entry '"<U006A><U0075><U006C>";"<U0061><U0067><U006F>";/ '
Error: Bad entry '"<U006A><U0075><U006C><U0069><U006F>";/ '
Error: Bad entry '"<U006A><U0075><U006E><U0069><U006F>";/ '
Error: Bad entry '"<U006C><U0075><U006E><U0065><U0073>";/ '
Error: Bad entry '"<U006D><U0061><U0072>";"<U0061><U0062><U0072>";/ '
Error: Bad entry '"<U006D><U0061><U0072>";"<U006D><U0069><U00E9>";/ '
Error: Bad entry '"<U006D><U0061><U0072><U0074><U0065><U0073>";/ '
Error: Bad entry '"<U006D><U0061><U0072><U007A><U006F>";/ '
Error: Bad entry '"<U006D><U0061><U0079>";"<U006A><U0075><U006E>";/ '
Error: Bad entry '"<U006D><U0061><U0079><U006F>";/ '
Error: Bad entry '"<U006D><U0069><U00E9><U0072><U0063><U006F><U006C><U0065><U0073>";/ '
Error: Bad entry '"<U006E><U006F><U0076>";"<U0064><U0069><U0063>" '
Error: Bad entry '"<U006E><U006F><U0076><U0069><U0065><U006D><U0062><U0072><U0065>";/ '
Error: Bad entry '"<U006F><U0063><U0074><U0075><U0062><U0072><U0065>";/ '
Error: Bad entry '"<U0073><U0065><U0070>";"<U006F><U0063><U0074>";/ '
Error: Bad entry '"<U0073><U0065><U0070><U0074><U0069><U0065><U006D><U0062><U0072><U0065>";/ '
Error: Bad entry '"<U0073><U00E1><U0062>" '
Error: Bad entry '"<U0073><U00E1><U0062><U0061><U0064><U006F>" '
Error: Bad entry '"<U0076><U0069><U0065><U0072><U006E><U0065><U0073>";/ '
Error: Bad entry '% '
sed: -e expression #1, char 36: unknown option to `s'


But I do not know where to find the file containing the Bad entries.
I have also tried to remove and reinstall locales but, as it tries to generate locales every time, the same error appears again and again. Is it possible that this is due to a dependency problem after updating to 8.04?

Can anyone help?

---

### Post by agent_shooter on 2008-11-17
Looking for teh same thing you were:

vi /var/lib/locales/supported.d/local

Then remove the "bad entries"

---

