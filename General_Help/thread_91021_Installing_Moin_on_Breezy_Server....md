---
title: "Installing Moin on Breezy Server..."
date: 2005-11-16
forum: General Help
---

### Post by butlershouse on 2005-11-16
I had trouble getting Moin ( a wiki available in the repositories ) . I had followed the instruction in the README.Debian file and could not get moin to work correctly . Some fiddling around with the config and heres my working entries which I placed in /etc/apache2/sites-available/default : inside the Virtualhost elements.

--- default entry ---
Alias /wiki/ "/usr/share/moin/htdocs/"
<Directory "/usr/share/moin/htdocs/">
   Order deny,allow
   Allow from all
</Directory>
<Directory "/var/local/lib/wiki">
   Order deny,allow
   Allow from all
</Directory>
<Location /wiki>
    SetHandler python-program
    # Add the path of your wiki directory
    PythonPath "['/var/local/lib/wiki', '/usr/lib/python2.4/site-packages'] + sys.path"
    PythonHandler MoinMoin.request::RequestModPy.run
    PythonInterpreter wiki
    PythonOption Location /wiki
</Location>

--- end extract ..


I also edited the moin.cfg and moin_config.py as follows

These entries are in /var/local/lib/wiki

moin.cgi : 

import sys
sys.path.append('/var/local/lib/wiki')
sys.path.insert(0, '/var/local/lib/wiki')

moin_config.py:
sitename = 'A Wiki for playing with '
interwikiname = None
#data_dir = './data/'
data_dir = '/var/local/lib/wiki/data/'
url_prefix = '/wiki'
httpd_host = "localhost"
httpd_port = 80
httpd_user = "www-data"
httpd_docs = "/usr/share/moin/htdocs/"


Hopefully this helps anyone else whom had to experience this . I will be posting these comments in moin moins relevant section just as soon as I can find it 

Nik

---

