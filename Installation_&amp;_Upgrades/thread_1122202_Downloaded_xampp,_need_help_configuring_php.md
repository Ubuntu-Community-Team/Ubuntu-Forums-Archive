---
title: "Downloaded xampp, need help configuring php"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by tkearn5000 on 2009-04-10
I downloaded xampp recently in order to test some php and mysql stuff that I am learning. I was wondering if anyone has experience reconfiguring the php so that I can use mysqli functions in my php documents. In windows this is something that is done during the installation.

If anyone knows how to do this, please let me know.

Thanks,
-TK

---

### Post by tkearn5000 on 2009-04-11
After more research, I've realized that I need to modify my php.ini file to include the mysqli.so extension.  I have done this and am still having no luck.

This is what I put in the php.ini file.


      extension_dir = /usr/lib/php5/20060613+lfs/    (this is the location of the mysqli.so file when i use the locate command)


and I wrote in:
      extension=php_mysqli.so

According to a tutorial on here, this is what I had to do to get mysqli working.

Now, however, I get this series of error messages when starting XAMPP, and the mysqli commands don't work in my php documents.



Starting XAMPP for Linux 1.7...
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/php_mysqli.so' - /usr/lib/php5/20060613+lfs/php_mysqli.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/zip.so' - /usr/lib/php5/20060613+lfs/zip.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/sqlite.so' - /usr/lib/php5/20060613+lfs/sqlite.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/radius.so' - /usr/lib/php5/20060613+lfs/radius.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/pgsql.so' - /usr/lib/php5/20060613+lfs/pgsql.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/dbx.so' - /usr/lib/php5/20060613+lfs/dbx.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/ming.so' - /usr/lib/php5/20060613+lfs/ming.so: cannot open shared object file: No such file or directory in Unknown on line 0
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Starting MySQL...
XAMPP: Starting ProFTPD...
XAMPP for Linux started.



Any help would be appreciated. 
Thanks
-TK

---

### Post by tkearn5000 on 2009-04-11
Obviously my extension_dir entry was causing those errors. But the original problem still exists of not being able to use mysqli functions in php docs.

---

