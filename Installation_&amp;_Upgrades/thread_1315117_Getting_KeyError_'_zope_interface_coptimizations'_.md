---
title: "Getting KeyError: '_zope_interface_coptimizations' with turbogears in ubuntu 9.10"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by naseemkkd on 2009-11-05
I am getting following error message when installing turbogears in ubuntu 9.10

```
Searching for zope.interface
Reading http://www.turbogears.org/2.0/downloads/current/index/zope.interface/
Best match: zope.interface 3.4.1
Downloading http://www.turbogears.org/2.0/downloads/current/zope.interface-3.4.1.tar.gz
Processing zope.interface-3.4.1.tar.gz
Running zope.interface-3.4.1/setup.py -q bdist_egg --dist-dir /tmp/easy_install-72_clB/zope.interface-3.4.1/egg-dist-tmp-Ms2o4o
Traceback (most recent call last):
  File "tg2env/bin/easy_install", line 8, in <module>
    load_entry_point('setuptools==0.6c9', 'console_scripts', 'easy_install')()
  File "/home/saleena/tg2env/lib/python2.6/site-packages/setuptools-0.6c9-py2.6.egg/setuptools/command/easy_install.py", line 1671, in main
  File "/home/saleena/tg2env/lib/python2.6/site-packages/setuptools-0.6c9-py2.6.egg/setuptools/command/easy_install.py", line 1659, in with_ei_usage
  File "/home/saleena/tg2env/lib/python2.6/site-packages/setuptools-0.6c9-py2.6.egg/setuptools/command/easy_install.py", line 1675, in <lambda>
  File "/usr/lib/python2.6/distutils/core.py", line 152, in setup
    dist.run_commands()
  File "/usr/lib/python2.6/distutils/dist.py", line 975, in run_commands
    self.run_command(cmd)
  File "/usr/lib/python2.6/distutils/dist.py", line 995, in run_command
    cmd_obj.run()
  File "/home/saleena/tg2env/lib/python2.6/site-packages/setuptools-0.6c9-py2.6.egg/setuptools/command/easy_install.py", line 211, in run
  File "/home/saleena/tg2env/lib/python2.6/site-packages/setuptools-0.6c9-py2.6.egg/setuptools/command/easy_install.py", line 446, in easy_install
  File "/home/saleena/tg2env/lib/python2.6/site-packages/setuptools-0.6c9-py2.6.egg/setuptools/command/easy_install.py", line 478, in install_item
  File "/home/saleena/tg2env/lib/python2.6/site-packages/setuptools-0.6c9-py2.6.egg/setuptools/command/easy_install.py", line 519, in process_distribution
  File "/home/saleena/tg2env/lib/python2.6/site-packages/setuptools-0.6c9-py2.6.egg/pkg_resources.py", line 522, in resolve
  File "/home/saleena/tg2env/lib/python2.6/site-packages/setuptools-0.6c9-py2.6.egg/pkg_resources.py", line 758, in best_match
  File "/home/saleena/tg2env/lib/python2.6/site-packages/setuptools-0.6c9-py2.6.egg/pkg_resources.py", line 770, in obtain
  File "/home/saleena/tg2env/lib/python2.6/site-packages/setuptools-0.6c9-py2.6.egg/setuptools/command/easy_install.py", line 446, in easy_install
  File "/home/saleena/tg2env/lib/python2.6/site-packages/setuptools-0.6c9-py2.6.egg/setuptools/command/easy_install.py", line 476, in install_item
  File "/home/saleena/tg2env/lib/python2.6/site-packages/setuptools-0.6c9-py2.6.egg/setuptools/command/easy_install.py", line 655, in install_eggs
  File "/home/saleena/tg2env/lib/python2.6/site-packages/setuptools-0.6c9-py2.6.egg/setuptools/command/easy_install.py", line 930, in build_and_install
  File "/home/saleena/tg2env/lib/python2.6/site-packages/setuptools-0.6c9-py2.6.egg/setuptools/command/easy_install.py", line 919, in run_setup
  File "/home/saleena/tg2env/lib/python2.6/site-packages/setuptools-0.6c9-py2.6.egg/setuptools/sandbox.py", line 27, in run_setup
  File "/home/saleena/tg2env/lib/python2.6/site-packages/setuptools-0.6c9-py2.6.egg/setuptools/sandbox.py", line 63, in run
  File "/home/saleena/tg2env/lib/python2.6/site-packages/setuptools-0.6c9-py2.6.egg/setuptools/sandbox.py", line 29, in <lambda>
  File "setup.py", line 85, in <module>
  File "/usr/lib/python2.6/distutils/core.py", line 152, in setup
    dist.run_commands()
  File "/usr/lib/python2.6/distutils/dist.py", line 975, in run_commands
    self.run_command(cmd)
  File "/usr/lib/python2.6/distutils/dist.py", line 995, in run_command
    cmd_obj.run()
  File "/home/saleena/tg2env/lib/python2.6/site-packages/setuptools-0.6c9-py2.6.egg/setuptools/command/bdist_egg.py", line 174, in run
  File "/home/saleena/tg2env/lib/python2.6/site-packages/setuptools-0.6c9-py2.6.egg/setuptools/command/bdist_egg.py", line 161, in call_command
  File "/usr/lib/python2.6/distutils/cmd.py", line 333, in run_command
    self.distribution.run_command(command)
  File "/usr/lib/python2.6/distutils/dist.py", line 995, in run_command
    cmd_obj.run()
  File "/home/saleena/tg2env/lib/python2.6/site-packages/setuptools-0.6c9-py2.6.egg/setuptools/command/install_lib.py", line 20, in run
  File "/usr/lib/python2.6/distutils/command/install_lib.py", line 113, in build
    self.run_command('build_ext')
  File "/usr/lib/python2.6/distutils/cmd.py", line 333, in run_command
    self.distribution.run_command(command)
  File "/usr/lib/python2.6/distutils/dist.py", line 995, in run_command
    cmd_obj.run()
  File "/home/saleena/tg2env/lib/python2.6/site-packages/setuptools-0.6c9-py2.6.egg/setuptools/command/build_ext.py", line 46, in run
  File "/usr/lib/python2.6/distutils/command/build_ext.py", line 340, in run
    self.build_extensions()
  File "/usr/lib/python2.6/distutils/command/build_ext.py", line 449, in build_extensions
    self.build_extension(ext)
  File "/home/saleena/tg2env/lib/python2.6/site-packages/setuptools-0.6c9-py2.6.egg/setuptools/command/build_ext.py", line 175, in build_extension
  File "/usr/lib/python2.6/distutils/command/build_ext.py", line 460, in build_extension
    ext_path = self.get_ext_fullpath(ext.name)
  File "/usr/lib/python2.6/distutils/command/build_ext.py", line 637, in get_ext_fullpath
    filename = self.get_ext_filename(ext_name)
  File "/home/saleena/tg2env/lib/python2.6/site-packages/setuptools-0.6c9-py2.6.egg/setuptools/command/build_ext.py", line 85, in get_ext_filename
KeyError: '_zope_interface_coptimizations'
```


I used following link for turbogears installation
[http://turbogears.org/2.0/docs/main/DownloadInstall.html]("http://turbogears.org/2.0/docs/main/DownloadInstall.html")

This error came when running the following command
$ python tg2-bootstrap.py --no-site-packages tg2env

Any idea about the issue

Thanks in advance
Naseem

---

### Post by brijith on 2009-11-18
Hi,
Check
         [http://groups.google.com/group/turbogears/browse_thread/thread/6dde3a2eebc478fb?pli=1](http://groups.google.com/group/turbogears/browse_thread/thread/6dde3a2eebc478fb?pli=1)

---

### Post by Krijk on 2010-01-01
Since I didn't want to downgrade to Python 2.5 fixed this with reinstalling easy_install using [http://peak.telecommunity.com/dist/ez_setup.py]("http://peak.telecommunity.com/dist/ez_setup.py")

This worked for me.

---

