---
title: "Mercurial Web Access failing pushing"
date: 2009-06-28
forum: Installation &amp; Upgrades
---

### Post by ddevore on 2009-06-28
I am running into a couple of problems with Mercurial web access, which was working with 8.04. I have looked for hours for a solution to this problem and even thought about some other solutions to the problem but have not found one that I liked as much as the web access. This is not a large project and it is just me working on it so I don't need a lot of speed, though the ssl would be nice. I think I have installed everything with the exception of the module for ssl because I don't know which module to install. I can see the repository via a browser and clone it but, I cannot push changes to it. Below are my configuration files and the errors I get when I commit. Any suggestions are welcome.

**These are the configuration files.**

_/etc/apache2/sites-enabled/000-default:_

	Include /landover/repo/hg/site.conf


_/landover/repo/hg/site.config_ 
(I also have one for ssl but like I said I don't know which module to install for it):

ScriptAliasMatch        ^/hg(.*)        /landover/repo/hg/hgwebdir.cgi$1

<Directory /landover/repo/hg>
  Options ExecCGI FollowSymLinks

  AllowOverride None
</Directory>


_/landover/repo/hg/hgweb.config:_

[collections]
/landover/repo/hg/TDCMidwest = TDCMidwest

[web]
style = gitweb
push_ssl=false
allow_push=*


_/landover/repo/hg/TDCMidwest/.hg/hgrc:_

[web]
allow_push = *
push_ssl = false


**These are the push commands with the errors.**

ddevore@giskard:/home/projects/tdc/TDCMidwest$ hg push
pushing to [http://foundation/hg/TDCMidwest](http://foundation/hg/TDCMidwest)
searching for changes
abort: HTTP Error 500: Internal Server Error

ddevore@giskard:/home/projects/TDCMidwest$ hg push --debug -v --traceback 
using [http://foundation/hg/TDCMidwest](http://foundation/hg/TDCMidwest)
sending between command
pushing to [http://foundation/hg/TDCMidwest](http://foundation/hg/TDCMidwest)
sending capabilities command
capabilities: unbundle=HG10GZ,HG10BZ,HG10UN lookup changegroupsubset
sending heads command
searching for changes
common changesets up to a0a583626186
1 changesets found
List of changesets:
d1c9d09306764fe1b2a19e39480b20e729f6301a
sending unbundle command
sending 4305 bytes
Traceback (most recent call last):
  File "/var/lib/python-support/python2.6/mercurial/dispatch.py", line 45, in _runcatch
    return _dispatch(ui, args)
  File "/var/lib/python-support/python2.6/mercurial/dispatch.py", line 367, in _dispatch
    ret = _runcommand(ui, options, cmd, d)
  File "/var/lib/python-support/python2.6/mercurial/dispatch.py", line 416, in _runcommand
    return checkargs()
  File "/var/lib/python-support/python2.6/mercurial/dispatch.py", line 376, in checkargs
    return cmdfunc()
  File "/var/lib/python-support/python2.6/mercurial/dispatch.py", line 361, in <lambda>
    d = lambda: util.checksignature(func)(ui, *args, **cmdoptions)
  File "/var/lib/python-support/python2.6/mercurial/util.py", line 715, in check
    return func(*args, **kwargs)
  File "/var/lib/python-support/python2.6/mercurial/commands.py", line 2211, in push
    r = repo.push(other, opts.get('force'), revs=revs)
  File "/var/lib/python-support/python2.6/mercurial/localrepo.py", line 1495, in push
    return self.push_unbundle(remote, force, revs)
  File "/var/lib/python-support/python2.6/mercurial/localrepo.py", line 1576, in push_unbundle
    return remote.unbundle(cg, remote_heads, 'push')
  File "/var/lib/python-support/python2.6/mercurial/httprepo.py", line 199, in unbundle
    heads=' '.join(map(hex, heads)))
  File "/var/lib/python-support/python2.6/mercurial/httprepo.py", line 119, in do_read
    fp = self.do_cmd(cmd, **args)
  File "/var/lib/python-support/python2.6/mercurial/httprepo.py", line 73, in do_cmd
    resp = self.urlopener.open(urllib2.Request(cu, data, headers))
  File "/usr/lib/python2.6/urllib2.py", line 389, in open
    response = meth(req, response)
  File "/usr/lib/python2.6/urllib2.py", line 502, in http_response
    'http', request, response, code, msg, hdrs)
  File "/usr/lib/python2.6/urllib2.py", line 427, in error
    return self._call_chain(*args)
  File "/usr/lib/python2.6/urllib2.py", line 361, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.6/urllib2.py", line 510, in http_error_default
    raise HTTPError(req.get_full_url(), code, msg, hdrs, fp)
HTTPError: HTTP Error 500: Internal Server Error
abort: HTTP Error 500: Internal Server Error

---

### Post by ddevore on 2009-06-30
I found the error. The files in the repository were not owned properly. I changed the owner to www-data and all appears to be working now.

From the repository root:
sudo chown -R www-data:www-data *

---

