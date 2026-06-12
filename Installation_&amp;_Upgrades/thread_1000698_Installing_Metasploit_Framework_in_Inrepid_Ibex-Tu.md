---
title: "Installing Metasploit Framework in Inrepid Ibex-Tutorial"
date: 2008-12-03
forum: Installation &amp; Upgrades
---

### Post by theravenproject on 2008-12-03
First we have to get subversion and build essential;
```
sudo apt-get install build-essential subversion
``` 

Now we need the Ruby requirements for Metasploit:
```
sudo apt-get install libruby rdoc libyaml-ruby libzlib-ruby libopenssl-ruby libdl-ruby libreadline-ruby libiconv-ruby rubygems sqlite3 libsqlite3-ruby libsqlite3-dev
```

Next, Ibex comes with a non-compatible default ruby install (Version 1.8.7) so you can get it from [ftp://ftp.ruby-lang.org/pub/ruby/1.8/ruby-1.8.6-p111.tar.bz2]("ftp://ftp.ruby-lang.org/pub/ruby/1.8/ruby-1.8.6-p111.tar.bz2") or use the following to do so automatically from the shell using wget:
```
wget ftp://ftp.ruby-lang.org/pub/ruby/1.8/ruby-1.8.6-p111.tar.bz2
```

Now we remove our previously installed Ruby package:
```
sudo apt-get remove ruby
```

Then we extract, configure, make, and install our new version:
```
    #tar -jvxf ruby-1.8.6-p111.tar.bz2

    #cd ruby-1.8.6-p111

    #./configure

    #make

    #sudo make install
```

Now to install metasploit:

```
svn co http://metasploit.com/svn/framework3/trunk/ metasploit-svn
``` and then lastly-

to check it out we will cd into the msf-svn directory and run the console!

```
cd metasploit-svn

      ./msfconsole
```

And that should bring up your console-from here on out rely on metasploits documentation for usage!

---

### Post by sam0vi on 2009-03-09
HI. I've found your post quite useful, but even though i followed your steps down to the letter, i can't get metasploit to work. whenever i try to run any of the interfaces i get errors. For msfconsole and msfgui i get

smv@max1:~/metasploit-svn$ ./msfgui
/home/smv/metasploit-svn/lib/rex/text.rb:1:in `require': no such file to load -- digest/md5 (LoadError)
	from /home/smv/metasploit-svn/lib/rex/text.rb:1
	from /home/smv/metasploit-svn/lib/rex.rb:44:in `require'
	from /home/smv/metasploit-svn/lib/rex.rb:44
	from ./msfgui:14:in `require'
	from ./msfgui:14

And for msfweb i get

smv@max1:~/metasploit-svn$ ./msfweb
./lib/rex/text.rb:1:in `require': no such file to load -- digest/md5 (LoadError)
	from ./lib/rex/text.rb:1
	from ./lib/rex.rb:44:in `require'
	from ./lib/rex.rb:44
	from ./lib/msf/core.rb:16:in `require'
	from ./lib/msf/core.rb:16
	from ./lib/msf/base.rb:19:in `require'
	from ./lib/msf/base.rb:19
	from ./msfweb:15:in `require'
	from ./msfweb:15

Any clues as to what this messages mean? I can't really understand what they mean. thanx

---

### Post by tekkenhead on 2009-03-12
I have metasploit installed in hardy heron and to have msfgui interface to work i had to also install the following packages libglade2-ruby and libgtk2-ruby. I hope this helps.

---

### Post by RaghuRam on 2009-04-30
I installed everything as per the stesp, and I also installed 
# apt-get install libgtk2-ruby libglade2-ruby

but msfconsole starts with  some errors about loading modules:

root@r00t3r:/home/aditya/metasploit-svn# ./msfconsole 
[*] WARNING! The following modules could not be loaded!

    /home/aditya/metasploit-svn/modules/auxiliary/scanner/telephony/wardial.rb: LoadError (eval):9:in `require': no such file to load -- zlib

    /home/aditya/metasploit-svn/modules/exploits/windows/fileformat/adobe_jbig2decode.rb: LoadError (eval):9:in `require': no such file to load -- zlib

    /home/aditya/metasploit-svn/modules/auxiliary/pdf/foxit/authbypass.rb: LoadError (eval):9:in `require': no such file to load -- zlib

    /home/aditya/metasploit-svn/modules/exploits/windows/browser/adobe_jbig2decode.rb: LoadError (eval):9:in `require': no such file to load -- zlib

    /home/aditya/metasploit-svn/modules/exploits/windows/fileformat/adobe_geticon.rb: LoadError (eval):9:in `require': no such file to load -- zlib

    /home/aditya/metasploit-svn/modules/exploits/windows/fileformat/adobe_utilprintf.rb: LoadError (eval):9:in `require': no such file to load -- zlib

    /home/aditya/metasploit-svn/modules/exploits/windows/browser/adobe_geticon.rb: LoadError (eval):9:in `require': no such file to load -- zlib

    /home/aditya/metasploit-svn/modules/exploits/windows/fileformat/adobe_collectemailinfo.rb: LoadError (eval):9:in `require': no such file to load -- zlib

    /home/aditya/metasploit-svn/modules/exploits/windows/browser/adobe_utilprintf.rb: LoadError (eval):9:in `require': no such file to load -- zlib

---

### Post by RaghuRam on 2009-05-01
I forgot to mention .. msfweb and msfgui didnt run because of errors. Now I managed to install ruby properly. I will write the steps. However my msfgui is still not running. I resinstalled gtk but ultimately it gave me this error:

```
root@r00t3r:/home/aditya/pentest/metasploit# ./msfgui
[*] The msfgui interface requires the ruby-gtk2 and ruby-libglade2 packages
[*] Dependencies include ruby-pango, ruby-glib2, ruby-gdkpixbuf2, and ruby-atk
[-] Error: LoadError /usr/lib/ruby/1.8/i486-linux/gtk2.so: undefined symbol: rbgobj_id_children - /usr/lib/ruby/1.8/i486-linux/gtk2.so
root@r00t3r:/home/aditya/pentest/metasploit# 
```

No clue on this.

---

### Post by RaghuRam on 2009-05-01
I will explain the way I installed everything.

1. First install the mentioned packages thru apt-get.
```
apt-get install ruby libruby rdoc libgtk2-ruby libglade2-ruby libyaml-ruby libzlib-ruby libopenssl-ruby libdl-ruby libreadline-ruby libiconv-ruby sqlite3 libsqlite3-ruby irb

```

Dont install rubygems from apt-get.

2. Then install ruby from source
[http://rubyforge.org/frs/download.php/55372/ruby-1.8.7-p160.tar.gz](http://rubyforge.org/frs/download.php/55372/ruby-1.8.7-p160.tar.gz)
3. THen install rubygem from source
[http://rubyforge.org/frs/download.php/55066/rubygems-1.3.2.tgz](http://rubyforge.org/frs/download.php/55066/rubygems-1.3.2.tgz)
4. then using gem, install rails.
```
gem install rails
```5. Check ur ruby/rail installation by this test script
```
rails testapp
```It will create a folder testapp
In it, run 
```
./script/server
```if u get no error, means ur basic ruby install was fine. Cant be sure about gtk.
6. Finally get msf through svn

In the 5th step while running msfconsole I got the zlib errors: 
This is what I did for the zlib errors. Also whenever I used gem, it gave me one of zlib errors:

```
/usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:31:in
`gem_original_require’: no such file to load — zlib (LoadError)
``` I resolved this by installing zlib package from here:

[http://linux.softpedia.com/progDownload/zlib-Download-159.html](http://linux.softpedia.com/progDownload/zlib-Download-159.html)

Btw, I got the clue after reading this page:
[URL="http://bluescripts.net/2009/03/ruby-ruby-on-rails/"]
http://bluescripts.net/2009/03/ruby-ruby-on-rails/[/URL]


So, after resolving zlib, it gave me an openssl error in step 5 :

 ```
`require_frameworks': no such file to load -- openssl (RuntimeError)
```I reached ruby-1.8.7-p160/ext/openssl in my ruby source folder, and ran 
```
ruby extconf.rb 
```THis checks whether your openssl configuration is perfect for the install or not. It gave me a missing file (ssl.h) errors.

THough Openssl was installed still I didnt have any source files anywhere . So I installed the development package for openssl.

```
apt-get install libssl-dev
```Again I went in the ruby source directory and used the following commands

```
make clean
./configure
make
make install
```THen go to the rubygems source, and run

```
ruby setup.rb
```This will install rubygems.

Install rails.

```
gem install rails
```Run the testapp Webrick server.

```
rails testapp
cd testapp
./script/server
```If this is successful, you can assume your ruby installation was fine.

---

### Post by RaghuRam on 2009-05-01
In case you see errors like this:

```
root@r00t3r:/home/aditya/pentest/metasploit# ./msfgui
[*] The msfgui interface requires the ruby-gtk2 and ruby-libglade2 packages
[*] Dependencies include ruby-pango, ruby-glib2, ruby-gdkpixbuf2, and ruby-atk
[-] Error: LoadError libruby1.8.so.1.8: cannot open shared object file: No such file or directory - /usr/lib/ruby/1.8/i486-linux/gtk2.so
```

You can check the libraries being used by ldd. I just found that I had accidentally removed one file.

```
ldd gtk2.so
    linux-gate.so.1 =>  (0xb8031000)
    libruby1.8.so.1.8 => not found
```

If some library is not found, that sure is a bad indication.

---

### Post by zenial on 2009-09-20
> **theravenproject said:**
> first we have to get subversion and build essential;
```
sudo apt-get install build-essential subversion
``` 

now we need the ruby requirements for metasploit:
```
sudo apt-get install libruby rdoc libyaml-ruby libzlib-ruby libopenssl-ruby libdl-ruby libreadline-ruby libiconv-ruby rubygems sqlite3 libsqlite3-ruby libsqlite3-dev
```

next, ibex comes with a non-compatible default ruby install (version 1.8.7) so you can get it from [ftp://ftp.ruby-lang.org/pub/ruby/1.8/ruby-1.8.6-p111.tar.bz2]("ftp://ftp.ruby-lang.org/pub/ruby/1.8/ruby-1.8.6-p111.tar.bz2") or use the following to do so automatically from the shell using wget:
```
wget ftp://ftp.ruby-lang.org/pub/ruby/1.8/ruby-1.8.6-p111.tar.bz2
```

now we remove our previously installed ruby package:
```
sudo apt-get remove ruby
```

then we extract, configure, make, and install our new version:
```
    #tar -jvxf ruby-1.8.6-p111.tar.bz2

    #cd ruby-1.8.6-p111

    #./configure

    #make

    #sudo make install
```

now to install metasploit:

```
svn co http://metasploit.com/svn/framework3/trunk/ metasploit-svn
``` and then lastly-

to check it out we will cd into the msf-svn directory and run the console!

```
cd metasploit-svn

      ./msfconsole
```

and that should bring up your console-from here on out rely on metasploits documentation for usage!:ks

---

