---
title: "GNU find: Suppress &quot;Permission denied&quot; + Script [SOLUTION]"
date: 2008-11-25
forum: General Help
---

### Post by natrik on 2008-11-25
[SIZE="4"]I came up with a way[/SIZE] to quell the plenitude of "[FONT="Courier New"]**Permission denied**[/FONT]" lines I constantly get  which only clog up my results from a[FONT="Courier New"] **find** [/FONT] command.  It's not something I want to type all the time, to be sure, and it will only work for Bourne family shells (and I'm fond of tcsh for interacting) so I put it in a script.  I call it[FONT="Courier New"]** qfind**[/FONT].  Please do understand how it's put together.  There's no warranty!

```
#!/bin/sh
# qfind 
# usage: just like find, but quells the bull. 
#        see 'man find'
#

/usr/bin/find $@ 2>&1 | grep -ve '^/usr/bin/find: .*: Permission denied$'

#^^^^^^^ full path here  ...       ^^^^^^^ or this won't match!
```

[SIZE="3"]**Explanation:**[/SIZE]
This calls[FONT="Courier New"]** find **[/FONT]with all the arguments passed along in[FONT="Courier New"]** $@ **[/FONT]. Then[FONT="Courier New"]** stderr **[/FONT]is redirected to[FONT="Courier New"]** stdout **[/FONT]with the construct[FONT="Courier New"]** 2>&1 **[/FONT]...  Then it's all piped to[FONT="Courier New"]** grep **[/FONT]which is given the[FONT="Courier New"]** -v **[/FONT](invert) switch to return all lines NOT matching, and the[FONT="Courier New"]** -e **[/FONT]switch to specify that a regular expression follows.

The regular expression (regex) is:[FONT="Courier New"]** _^/usr/bin/find: .*: Permission denied$_**[/FONT]

[FONT="Courier New"]**_^_ **[/FONT]= matches the beginning of the line
[FONT="Courier New"]**_/usr/bin/find: _**[/FONT]= literal text including trailing colon, space -- This is matched by an explicit call to[FONT="Courier New"] /usr/bin/find[/FONT], but not just [FONT="Courier New"] find[/FONT] !!
[FONT="Courier New"]**_.*_ **[/FONT] = matches any character, zero times or more; whatever you don't have permissions for is matched by this.
[FONT="Courier New"]**_: Permission denied_**[/FONT] = literal text.  Again, the colon and space are part of the literal pattern to oppress; they are not special.
[FONT="Courier New"]**_$_ **[/FONT] = matches the end of the line.

Beware the special case: I suppose it *could* be possible for legitimate[FONT="Courier New"] find [/FONT]results to be filtered out.  This is the primary reason for using the full path[FONT="Courier New"]** /usr/bin/find **[/FONT]because it will show up in the error output (along with the trailing colon and space), and be searched for to filter out.  This makes it *hella unlikely* that a false hit would really happen. But it's not technically impossible. And I know it's a little inelegant overall, but until there's a[FONT="Courier New"] find [/FONT]option like[FONT="Courier New"] --screw-permissions[/FONT], this will work just dandy for me.  :o)

[SIZE="3"]**Why Bother:**[/SIZE]
Surely I have not scoured the ENTIRE internet, but nowhere have I found this solution.  I have found lots of redirecting all[FONT="Courier New"] stderr [/FONT]to the[FONT="Courier New"] /dev/null [/FONT]device.  Of course then you get no error messages at all.  This here crafty workaround though, allows other errors to show up. With[FONT="Courier New"] find [/FONT]particularly, I'm prone to incite other errors at a frightening clip, so I want to know about them.  Meanwhile when I do figure out what I'm doing, the results are useful because they contain only my results.

I hope that someone out there is clever enough to come up with an elegant way to redirect the[FONT="Courier New"] stderr [/FONT] separate from[FONT="Courier New"] stdout [/FONT] altogether.  I'm surprised not to have found anything of the sort.  That would be very useful in general, no?  If anyone can show me a way to do that (or even how to do *this* in csh / tcsh) then please share!  This works for my case though, so I'm putting it somewhere google can[FONT="Courier New"]** find **[/FONT] it.  :o)

[SIZE="3"]Edify yourself further: [COLOR="DarkOrange"]**_[regex]("http://www.regular-expressions.info/tutorial.html")_ . _[redirection]("http://www.mathinfo.u-picardie.fr/asch/f/MeCS/courseware/users/help/general/unix/redirection.html")_**
[/COLOR]
Enjoy![/SIZE]

------------

In case you're interested, it was laziness that got me started on this:
```
#!/bin/sh
# wheresmy
# usage: wheresmy term [term2] [term3]
#

FILTER_OUT="^/usr/bin/find: .*: Permission denied$"

/usr/bin/find /media1 -iname '*'$1'*'$2'*'$3'*' 2>&1| grep -ve "$FILTER_OUT"
/usr/bin/find /media2 -iname '*'$1'*'$2'*'$3'*' 2>&1| grep -ve "$FILTER_OUT"
```


This way, I can be lazy, er, I mean ... I can find my media files quickly and effectively!  
For example, I want to know the path to Nodame Cantabile, episode 3, but alas, I can't spell at all.  I just type in a good guess:

[FONT="Courier New"]**wheresmy nod cant 03**[/FONT]

and i quickly get my result:

[FONT="Courier New"]**/media2/anime/Nodame Cantabile/Nodame_Cantabile_-_03.mkv**[/FONT]

If only one term is specified, it's inelegant, but still works just fine.  The * wildcards simply pile up like this: [FONT="Courier New"] *oneterm*** [/FONT] which probably wastes some CPU cycles, but has no effect on the output.  

Now to find my keys ...

-- Nate

---

