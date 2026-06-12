---
title: "Python 3.1 with ssl support"
date: 2009-07-19
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2009-07-19
I am trying to build Python 3.1 with ssl support, but nothing I try works.

I have modified Modules/Setup.dist to enable ssl support and set the include files and libraries to the appropriate place for Ubuntu (I think). 
--------------------Setup.dist snippet -----------------------
# Socket module helper for socket(2)
_socket socketmodule.c

# Socket module helper for SSL support; you must comment out the other
# socket line above, and possibly edit the SSL variable:
#SSL=
_ssl _ssl.c \
        -DUSE_SSL -I/usr/include \
        -L/usr/lib -lssl -lcrypto
---------------------------------------------------------------

I get no compile or link errors, but when I try this out I get the following:

-------------- Test ------------------
llist@LeosPc:/usr$ python3.1
Python 3.1 (r31:73572, Jul 20 2009, 12:27:32) 
[GCC 4.3.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import socket
>>> socket.ssl
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'module' object has no attribute 'ssl'
>>> 
-----------------------------------------

Thanks

---

### Post by meastwood on 2009-08-11
Do not know if this helps - ssl is a separate module to socket - so need to 
import ssl
see: [http://docs.python.org/3.1/library/ssl.html?highlight=ssl#module-ssl](http://docs.python.org/3.1/library/ssl.html?highlight=ssl#module-ssl)
###################################
import socket, ssl, pprint

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# require a certificate from the server
ssl_sock = ssl.wrap_socket(s,
                           ca_certs="/etc/ca_certs_file",
                           cert_reqs=ssl.CERT_REQUIRED)

ssl_sock.connect(('www.verisign.com', 443))

print(repr(ssl_sock.getpeername()))
pprint.pprint(ssl_sock.getpeercert())
print(pprint.pformat(ssl_sock.getpeercert()))

# Set a simple HTTP request -- use http.client in actual code.
ssl_sock.write("""GET / HTTP/1.0\r
Host: www.verisign.com\r\n\r\n""")

# Read a chunk of data.  Will not necessarily
# read all the data returned by the server.
data = ssl_sock.read()

# note that closing the SSLSocket will also close the underlying socket
ssl_sock.close()
########################################################### (from python.org)


Maybe you can help me ...

I'm wanting to install python3.1 - specifically for ttk support.  Have tried build ing from source using python3.1_3.1.orig.tar.gz(ubuntu)  Python-3.1.tar.bz2(python.org) but keep getting
..........
Python build finished, but the necessary bits to build these modules were not found:
_curses            _curses_panel      _dbm            
_gdbm              _hashlib           _sqlite3        
_ssl               _tkinter           bz2             
readline                                              
To find the necessary bits, look in setup.py in detect_modules() for the module's name.
The thing is I do not know where to get the header files for the 'bits'.

---

### Post by phillw on 2009-08-11
Python have a section on SSL ....

[http://docs.python.org/3.1/library/ssl.html](http://docs.python.org/3.1/library/ssl.html)

Hope that is of help.

Regards,

Phill.

---

### Post by meastwood on 2009-08-11
Just managed to sort 3.1 out - to get all modules compiled had to install

Unpacking python-openssl (from .../python-openssl_0.7-2ubuntu1_i386.deb) ...
Unpacking libncurses5-dev (from .../libncurses5-dev_5.7+20090207-1ubuntu1_i386.deb) ...
Unpacking libbz2-dev (from .../libbz2-dev_1.0.5-1ubuntu1_i386.deb) ...
Unpacking libreadline5-dev (from .../libreadline5-dev_5.2-4_i386.deb) ...
Unpacking libsqlite3-dev (from .../libsqlite3-dev_3.6.10-1ubuntu0.2_i386.deb) ...
Unpacking libssl-dev (from .../libssl-dev_0.9.8g-15ubuntu3.2_i386.deb) ...
Unpacking libgdbm-dev (from .../libgdbm-dev_1.8.3-4_i386.deb) ...
Unpacking tcl8.5-dev (from .../tcl8.5-dev_8.5.6-3_i386.deb) ...
Unpacking tk8.5-dev (from .../tk8.5-dev_8.5.6-3_i386.deb) ...

#./configure
#make
#sudo make altinstall

Did not do anything extra in terms of configuration  - for ssl

mark@ubudev:/usr/local$ python3.1
Python 3.1 (r31:73572, Aug 11 2009, 15:37:50) 
[GCC 4.3.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import ssl
>>> import sys
>>> sys.modules.keys()
dict_keys(['base64', 'sre_compile', '_sre', '__main__', 'site', '_ssl', 'io', 'encodings', 'copyreg', '_weakref', 'abc', 'builtins', 'posixpath', 'linecache', 'errno', '_socket', 'binascii', 'sre_constants', 're', 'encodings.latin_1', 'tokenize', '_struct', 'genericpath', 'stat', 'zipimport', 'string', '_codecs', 'encodings.utf_8', 'textwrap', 'sys', 'ssl', 'codecs', 'readline', 'os.path', 'struct', 'socket', 'signal', 'traceback', '_io', '_weakrefset', 'token', 'posix', 'encodings.aliases', 'sre_parse', 'os', '_abcoll'])
>>>

---

