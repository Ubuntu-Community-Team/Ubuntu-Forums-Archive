---
title: "[SOLVED] Invalid Commmand &amp;quot;ScriptAlias&amp;quot; / &amp;quot;Alias&amp;quot;"
date: 2008-08-23
forum: General Help
---

### Post by riyapiko on 2008-08-23
The problems that I'm facing is that I get this Error, when I start-up apache2, that states

Invalid command 'ScriptAlias', perhaps mis-spelled or defined by a module not included in the server configuration

I used the default configuration in /etc/apache2/sites-available/ and it returned the same error.

I get a similar error except its "Alias" this time, when i 'aptitude install phpmyadmin', thus my phpmyadmin doesnt work correctly.

please help! thanks

PS I am using the latest JeOS on VMware

---

### Post by RealPSL on 2008-08-23
This sounds to me like the supporting module for Alias and ScriptAlias is not loaded and the calls were not wrapped in "IfModule" tags. I would recommend you make sure that the mod_alias module is enabled by checking the /etc/apache2/mods-enabled directory. You will need to check for the existence of the alias.load file which should have the content:

> LoadModule alias_module /usr/lib/apache2/modules/mod_alias.so

You should also ensure that the file exists with
```
ls -l /usr/lib/apache2/modules/mod_alias.so
```

I am not a JeOS expert but I know it is a minimized OS for preparing appliances and virtual machines so maybe it just was not installed. If that is the case you should install it to get the functionality.

---

### Post by riyapiko on 2008-08-23
THANK YOU for your help!! As you said, the 'alias.load' was blank and after i added

'LoadModule alias_module /usr/lib/apache2/modules/mod_alias.so'

and restarted apache2, no error was returned this time!

thanks for the help.

---

