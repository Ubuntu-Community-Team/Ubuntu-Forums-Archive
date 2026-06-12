---
title: "Pear"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by veilig on 2009-11-12
I want to install pear.  I know how to ```
sudo apt-get install php-pear
```

problem is, now I have to ```
sudo pear install <packagename>
```

when I tried installing PHPUnit with this method I could only execute ```
sudo phpunit
``` because all my phpunit files were now in /usr/share/php/PEAR/PHPUnit which had root::root ownership and group.  if I tried without sudo I get this error.

```
Warning: require_once(PHPUnit/Util/Filter.php): failed to open stream: No such file or directory in /usr/bin/phpunit on line 43

Call Stack:
    0.0002     116856   1. {main}() /usr/bin/phpunit:0


Fatal error: require_once(): Failed opening required 'PHPUnit/Util/Filter.php' (include_path='.:/usr/share/php:/usr/share/pear') in /usr/bin/phpunit on line 43

Call Stack:
    0.0002     116856   1. {main}() /usr/bin/phpunit:0

```

obviously I can't access these files b/c I'm not a superuser.  how do I get around this?
This lovely [[COLOR="Blue"]doc[/COLOR] ]("https://help.ubuntu.com/community/PhpPear") leads me to believe I should be able to run pear as my normal user (installing packages and such) w/out the need to sudo

---

