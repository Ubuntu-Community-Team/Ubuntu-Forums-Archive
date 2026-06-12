---
title: "Sub-process /usr/bin/dpkg returned an error code for apt-get"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by raghaven.kumar on 2009-06-16
Hi ,
I get this long error when i install anything on ubuntu server 6.06.2 LTS
The package that i give installs good but returns this error whenever i do apt-get install.
Whats wrong
The below result is *apt-get -f install*.
```
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up python2.4-pysqlite2 (2.0.5-1ubuntu1) ...
Compiling /usr/lib/python2.4/site-packages/Products.CacheSetup-1.2-py2.4.egg/Products/CacheSetup/skins/cache_setup/cache_policy_redirect.py ...
  File "/usr/lib/python2.4/site-packages/Products.CacheSetup-1.2-py2.4.egg/Products/CacheSetup/skins/cache_setup/cache_policy_redirect.py", line 15
    return ct.setDisplayPolicy(policy_id, camefrom=camefrom, redirect=True)
SyntaxError: 'return' outside function

Compiling /usr/lib/python2.4/site-packages/Products.CacheSetup-1.2-py2.4.egg/Products/CacheSetup/skins/cache_setup/enableHTTPCompression.py ...
  File "/usr/lib/python2.4/site-packages/Products.CacheSetup-1.2-py2.4.egg/Products/CacheSetup/skins/cache_setup/enableHTTPCompression.py", line 23
    return '<!-- compression status: disabled -->'
SyntaxError: 'return' outside function

Compiling /usr/lib/python2.4/site-packages/Products.CacheSetup-1.2-py2.4.egg/Products/CacheSetup/skins/cache_setup/getFolderButtons.py ...
  File "/usr/lib/python2.4/site-packages/Products.CacheSetup-1.2-py2.4.egg/Products/CacheSetup/skins/cache_setup/getFolderButtons.py", line 21
    return actions
SyntaxError: 'return' outside function

Compiling /usr/lib/python2.4/site-packages/Products.CacheSetup-1.2-py2.4.egg/Products/CacheSetup/skins/cache_setup/getHeaderSetIdForResource.py ...
  File "/usr/lib/python2.4/site-packages/Products.CacheSetup-1.2-py2.4.egg/Products/CacheSetup/skins/cache_setup/getHeaderSetIdForResource.py", line 16
    return None
SyntaxError: 'return' outside function

Compiling /usr/lib/python2.4/site-packages/Products.CacheSetup-1.2-py2.4.egg/Products/CacheSetup/skins/cache_setup/getImageAndFilePurgeUrls.py ...
  File "/usr/lib/python2.4/site-packages/Products.CacheSetup-1.2-py2.4.egg/Products/CacheSetup/skins/cache_setup/getImageAndFilePurgeUrls.py", line 11
    return []
SyntaxError: 'return' outside function

Compiling /usr/lib/python2.4/site-packages/Products.CacheSetup-1.2-py2.4.egg/Products/CacheSetup/skins/cache_setup/getUncataloguedFolderContents.py ...
  File "/usr/lib/python2.4/site-packages/Products.CacheSetup-1.2-py2.4.egg/Products/CacheSetup/skins/cache_setup/getUncataloguedFolderContents.py", line 17
    return batch
SyntaxError: 'return' outside function

Compiling /usr/lib/python2.4/site-packages/Products.CacheSetup-1.2-py2.4.egg/Products/CacheSetup/skins/cache_setup/rewritePurgeUrls.py ...
  File "/usr/lib/python2.4/site-packages/Products.CacheSetup-1.2-py2.4.egg/Products/CacheSetup/skins/cache_setup/rewritePurgeUrls.py", line 65
    return rewrite_legacy(relative_urls, domains)
SyntaxError: 'return' outside function

dpkg: error processing python2.4-pysqlite2 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-pysqlite2:
 python-pysqlite2 depends on python2.4-pysqlite2; however:
  Package python2.4-pysqlite2 is not configured yet.
dpkg: error processing python-pysqlite2 (--configure):
 dependency problems - leaving unconfigured
Setting up python-subversion (1.3.2-3ubuntu2~dapper1) ...
Compiling /usr/lib/python2.4/site-packages/Products.CacheSetup-1.2-py2.4.egg/Products/CacheSetup/skins/cache_setup/cache_policy_redirect.py ...
  File "/usr/lib/python2.4/site-packages/Products.CacheSetup-1.2-py2.4.egg/Products/CacheSetup/skins/cache_setup/cache_policy_redirect.py", line 15
    return ct.setDisplayPolicy(policy_id, camefrom=camefrom, redirect=True)
SyntaxError: 'return' outside function

Compiling /usr/lib/python2.4/site-packages/Products.CacheSetup-1.2-py2.4.egg/Products/CacheSetup/skins/cache_setup/enableHTTPCompression.py ...
  File "/usr/lib/python2.4/site-packages/Products.CacheSetup-1.2-py2.4.egg/Products/CacheSetup/skins/cache_setup/enableHTTPCompression.py", line 23
    return '<!-- compression status: disabled -->'
SyntaxError: 'return' outside function

Compiling /usr/lib/python2.4/site-packages/Products.CacheSetup-1.2-py2.4.egg/Products/CacheSetup/skins/cache_setup/getFolderButtons.py ...
  File "/usr/lib/python2.4/site-packages/Products.CacheSetup-1.2-py2.4.egg/Products/CacheSetup/skins/cache_setup/getFolderButtons.py", line 21
    return actions
SyntaxError: 'return' outside function

Compiling /usr/lib/python2.4/site-packages/Products.CacheSetup-1.2-py2.4.egg/Products/CacheSetup/skins/cache_setup/getHeaderSetIdForResource.py ...
  File "/usr/lib/python2.4/site-packages/Products.CacheSetup-1.2-py2.4.egg/Products/CacheSetup/skins/cache_setup/getHeaderSetIdForResource.py", line 16
    return None
SyntaxError: 'return' outside function

Compiling /usr/lib/python2.4/site-packages/Products.CacheSetup-1.2-py2.4.egg/Products/CacheSetup/skins/cache_setup/getImageAndFilePurgeUrls.py ...
  File "/usr/lib/python2.4/site-packages/Products.CacheSetup-1.2-py2.4.egg/Products/CacheSetup/skins/cache_setup/getImageAndFilePurgeUrls.py", line 11
    return []
SyntaxError: 'return' outside function

Compiling /usr/lib/python2.4/site-packages/Products.CacheSetup-1.2-py2.4.egg/Products/CacheSetup/skins/cache_setup/getUncataloguedFolderContents.py ...
  File "/usr/lib/python2.4/site-packages/Products.CacheSetup-1.2-py2.4.egg/Products/CacheSetup/skins/cache_setup/getUncataloguedFolderContents.py", line 17
    return batch
SyntaxError: 'return' outside function

Compiling /usr/lib/python2.4/site-packages/Products.CacheSetup-1.2-py2.4.egg/Products/CacheSetup/skins/cache_setup/rewritePurgeUrls.py ...
  File "/usr/lib/python2.4/site-packages/Products.CacheSetup-1.2-py2.4.egg/Products/CacheSetup/skins/cache_setup/rewritePurgeUrls.py", line 65
    return rewrite_legacy(relative_urls, domains)
SyntaxError: 'return' outside function

dpkg: error processing python-subversion (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of trac:
 trac depends on python-pysqlite2 | python-sqlite (>= 0.4.3) | python2.4-psycopg; however:
  Package python-pysqlite2 is not configured yet.
  Package python-sqlite is not installed.
  Package python2.4-psycopg is not installed.
dpkg: error processing trac (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python2.4-pysqlite2
 python-pysqlite2
 python-subversion
 trac
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

