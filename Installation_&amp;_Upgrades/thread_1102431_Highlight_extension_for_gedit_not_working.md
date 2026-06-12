---
title: "Highlight extension for gedit not working"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by Flame_Phoenix on 2009-03-21
Hi guys, I use gedit for some time and I think it is quite good, specially with the syntax highlight which I really need and appreciate. However I work with many languages and so gedit does not have highlight plugins(don't know if this is the correct term) for them all, which is why I decided to create my own highlight for gedit. Basically, I made a search on internet and found this tutorial:

[http://live.gnome.org/Gedit/NewLanguage](http://live.gnome.org/Gedit/NewLanguage)

Which leaded me to:

[http://library.gnome.org/devel/gtksourceview-2.0/stable/lang-tutorial.html](http://library.gnome.org/devel/gtksourceview-2.0/stable/lang-tutorial.html)

My steps:
 - I installed Ubuntu (I am working on it now) made all updates, installed vBoxGuestEditions and then searched the tutorial
 - I read the tutorial and after that I created the following .lang file:

```
<?xml version="1.0" encoding="UTF-8"?>

	<language id="vJass" _name="vJass" version="2.0" _section="Others">

	<metadata>
		<property name="mimetypes">text/x-c;text/x-csrc;image/x-xpixmap</property>
	      	<property name="globs">*.vJass</property>
    	</metadata>
	
	<styles>
		<style id="comment" 		_name="Comment" 	map-to="def:comment"/>
		<style id="string"		_name="String" 		map-to="def:string"/>
		<style id="escape"  		_name="Escape" 		map-to="def:escape"/>
		<style id="preprocessor" 	_name="Preprocessor" 	map-to="def:preprocessor"/>
		<style id="included-file"	_name="Included File"	map-to="def:package"/>
		<style id="char" 		_name="Character"	map-to="def:string"/>
		<style id="keyword" 		_name="Keyword"		map-to="def:keyword"/>
		<style id="data-type" 		_name="Data Type"	map-to="def:data-type"/>
    	</styles>

	<definitions>
		<context id="vJass">
			<include>
			
			<context id="comment" style-ref="comment">
    				<start>\/\/</start>
    				<end>$</end>
			</context>

			<context id="string" end-at-line-end="true"
        			style-ref="string">
				
				<start>"</start>
				<end>"</end>

				<include>
					<context id="escape" style-ref="escape">
        					<match>\\.</match>
    					</context>
				</include>
			</context>

			<context id="keywords" style-ref="keyword">
				<keyword>if</keyword>
				<keyword>then</keyword>
			    	<keyword>else</keyword>
				<keyword>endif</keyword>
				<keyword>loop</keyword>
				<keyword>exitwhen</keyword>
				<keyword>endloop</keyword>
				<keyword>return</keyword>
				<keyword>debug</keyword>
				<keyword>globals</keyword>
				<keyword>endglobals</keyword>
				<keyword>scope</keyword>
				<keyword>endscope</keyword>
				<keyword>library</keyword>
				<keyword>endlibrary</keyword>
				<keyword>function</keyword>
				<keyword>endfunction</keyword>
				<keyword>private</keyword>
				<keyword>public</keyword>
				<keyword>call</keyword>
				<keyword>struct</keyword>
				<keyword>endstruct</keyword>
				<keyword>method</keyword>
				<keyword>endmethod</keyword>
				<keyword>constant</keyword>
				<keyword>static</keyword>
				<keyword>onDestroy</keyword>
				<keyword>interface</keyword>
				<keyword>endinterface</keyword>
				<keyword>native</keyword>
			</context>

			<context id="types" style-ref="data-type">
				<keyword>integer</keyword>
			    	<keyword>real</keyword>
				<keyword>string</keyword>
			    	<keyword>location</keyword>
				<keyword>group</keyword>
				<keyword>unit</keyword>
				<keyword>widget</keyword>
				<keyword>handle</keyword>
				<keyword>boolexpr</keyword>
				<keyword>boolean</keyword>
				<keyword>takes</keyword>
				<keyword>nothing</keyword>
			</context>

		</include>
		</context>
	</definitions>
	</language>		

```

After creating this file I did:
1 - closed gedit
2 - copied the file into "/usr/share/gtksourceview-2.0/language-specs" without the "" things. 
3 - opened gedit
4 - tested the file. When I go to "View -> highlight -> Others" I find "vJass" (yeeeye!) but then when I start writing code nothing happens. The text never gets colored. Can some one please tell me what is wrong with the code? Or if I did some step wrong?

Also, I based myself on some sections of the C.lang file from gedit, which is here:
```

<?xml version="1.0" encoding="UTF-8"?>
<!--

 Authors: Marco Barisione, Emanuele Aina
 Copyright (C) 2005-2007 Marco Barisione <barisione@gmail.com>
 Copyright (C) 2005-2007 Emanuele Aina

 This library is free software; you can redistribute it and/or
 modify it under the terms of the GNU Library General Public
 License as published by the Free Software Foundation; either
 version 2 of the License, or (at your option) any later version.

 This library is distributed in the hope that it will be useful,
 but WITHOUT ANY WARRANTY; without even the implied warranty of
 MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
 Library General Public License for more details.

 You should have received a copy of the GNU Library General Public
 License along with this library; if not, write to the
 Free Software Foundation, Inc., 59 Temple Place - Suite 330,
 Boston, MA 02111-1307, USA.

-->
<language id="c" _name="C" version="2.0" _section="Sources">
    <metadata>
      <property name="mimetypes">text/x-c;text/x-csrc;image/x-xpixmap</property>
      <property name="globs">*.c</property>
      <property name="line-comment-start">//</property>
      <property name="block-comment-start">/*</property>
      <property name="block-comment-end">*/</property>
    </metadata>

    <styles>
        <style id="comment"           _name="Comment"             map-to="def:comment"/>
        <style id="error"             _name="Error"               map-to="def:error"/>
        <style id="string"            _name="String"              map-to="def:string"/>
        <style id="preprocessor"      _name="Preprocessor"        map-to="def:preprocessor"/>
        <style id="common-defines"    _name="Common Defines"      map-to="def:special-constant"/>
        <style id="included-file"     _name="Included File"       map-to="def:string"/>
        <style id="char"              _name="Character"           map-to="def:character"/>
        <style id="keyword"           _name="Keyword"             map-to="def:keyword"/>
        <style id="type"              _name="Data Type"           map-to="def:type"/>
        <style id="storage-class"     _name="Storage Class"       map-to="def:type"/>
        <style id="printf"            _name="printf Conversion"   map-to="def:special-char"/>
        <style id="escaped-character" _name="Escaped Character"   map-to="def:special-char"/>
        <style id="floating-point"    _name="Floating point number" map-to="def:floating-point"/>
        <style id="decimal"           _name="Decimal number"      map-to="def:decimal"/>
        <style id="octal"             _name="Octal number"        map-to="def:base-n-integer"/>
        <style id="hexadecimal"       _name="Hexadecimal number"  map-to="def:base-n-integer"/>
        <style id="boolean"           _name="Boolean value"       map-to="def:boolean"/>
    </styles>

    <definitions>
        <!-- TODO: what about scanf ? -->
        <!-- man 3 printf -->
        <context id="printf" style-ref="printf" extend-parent="false">
            <match extended="true">
                \%\%|\%
                (?:[1-9][0-9]*\$)?      # argument
                [#0\-\ \+\'I]*          # flags
                (?:[1-9][0-9]*|\*)?     # width
                (?:\.\-?(?:[0-9]+|\*))? # precision
                (?:hh|ll|[hlLqjzt])?    # length modifier
                [diouxXeEfFgGaAcsCSpnm] # conversion specifier
            </match>
        </context>

        <define-regex id="escaped-character" extended="true">
            \\(                   # leading backslash
            [\\\"\'nrbtfav\?] |   # escaped character
            [0-7]{1,3} |          # one, two, or three octal digits
            x[0-9A-Fa-f]+         # 'x' followed by hex digits
            )
        </define-regex>

        <context id="c">
            <include>

                <!-- gtk-doc -->
                <context ref="gtk-doc:inline-docs-section"/>

                <!-- Comments -->
                <context id="comment" style-ref="comment" end-at-line-end="true">
                    <start>//</start>
                    <include>
                      <context ref="def:in-line-comment"/>
                    </include>
                </context>

                <context id="comment-multiline" style-ref="comment">
                    <start>/\*</start>
                    <end>\*/</end>
                    <include>
                        <context ref="def:in-comment"/>
                    </include>
                </context>

                <context id="close-comment-outside-comment" style-ref="error">
                    <match>\*/(?!\*)</match>
                </context>

                <!-- Preprocessor -->
                <define-regex id="preproc-start">^\s*#\s*</define-regex>

                <context id="if0-comment" style-ref="comment">
                    <start>\%{preproc-start}if\b\s*0\b</start>
                    <end>\%{preproc-start}(endif|else|elif)\b</end>
                    <include>
                        <context id="if-in-if0">
                            <start>\%{preproc-start}if(n?def)?\b</start>
                            <end>\%{preproc-start}endif\b</end>
                            <include>
                                <context ref="if-in-if0"/>
                                <context ref="def:in-comment"/>
                            </include>
                        </context>
                        <context ref="def:in-comment"/>
                    </include>
                </context>

                <context id="include" style-ref="preprocessor">
                    <match extended="true">
                            \%{preproc-start}
                            (include|import)\s*
                            (".*?"|&lt;.*&gt;)
                    </match>
                    <include>
                        <context id="included-file" sub-pattern="2" style-ref="included-file"/>
                    </include>
                </context>

                <context id="preprocessor" style-ref="preprocessor" end-at-line-end="true">
                    <start extended="true">
                            \%{preproc-start}
                            (define|undef|error|pragma|ident|if(n?def)?|else|elif|endif|line|warning)
                            \b
                    </start>
                    <include>
                        <context ref="def:line-continue" ignore-style="true"/>
                        <context ref="string" ignore-style="true"/>
                        <context ref="comment"/>
                        <context ref="comment-multiline"/>
                    </include>
                </context>

                <context id="string" style-ref="string" end-at-line-end="true">
                    <start>L?"</start>
                    <end>"</end>
                    <include>
                        <context ref="printf"/>
                        <context id="escaped-character" style-ref="escaped-character">
                            <match>\%{escaped-character}</match>
                        </context>
                        <context ref="def:line-continue"/>
                    </include>
                </context>

                <context id="char" style-ref="char">
                    <match>L?'(\%{escaped-character}|.)'</match>
                </context>

                <!-- http://www.lysator.liu.se/c/ANSI-C-grammar-l.html -->
                <context id="float" style-ref="floating-point">
                    <match extended="true">
                        (?&lt;![\w\.])
                        ((\.[0-9]+ | [0-9]+\.[0-9]*) ([Ee][+-]?[0-9]*)? |
                         ([0-9]+[Ee][+-]?[0-9]*))
                        [fFlL]?
                        (?![\w\.])
                    </match>
                </context>

                <context id="hexadecimal" style-ref="hexadecimal">
                    <match extended="true">
                        (?&lt;![\w\.])
                        0[xX][a-fA-F0-9]+[uUlL]*
                        (?![\w\.])
                    </match>
                </context>

                <context id="octal" style-ref="octal">
                    <match extended="true">
                        (?&lt;![\w\.])
                        0[0-7]+[uUlL]*
                        (?![\w\.])
                    </match>
                </context>

                <context id="decimal" style-ref="decimal">
                    <match extended="true">
                        (?&lt;![\w\.])
                        [0-9]+[uUlL]*
                        (?![\w\.])
                    </match>
                </context>

                <!-- Keywords -->
                <context id="keywords" style-ref="keyword">
                    <keyword>asm</keyword>
                    <keyword>break</keyword>
                    <keyword>case</keyword>
                    <keyword>continue</keyword>
                    <keyword>default</keyword>
                    <keyword>do</keyword>
                    <keyword>else</keyword>
                    <keyword>enum</keyword>
                    <keyword>for</keyword>
                    <keyword>fortran</keyword>
                    <keyword>goto</keyword>
                    <keyword>if</keyword>
                    <keyword>return</keyword>
                    <keyword>sizeof</keyword>
                    <keyword>struct</keyword>
                    <keyword>switch</keyword>
                    <keyword>typedef</keyword>
                    <keyword>union</keyword>
                    <keyword>while</keyword>
                </context>

                <context id="types" style-ref="type">
                    <keyword>_Bool</keyword>
                    <keyword>_Complex</keyword>
                    <keyword>_Imaginary</keyword>
                    <keyword>bool</keyword>
                    <keyword>char</keyword>
                    <keyword>double</keyword>
                    <keyword>float</keyword>
                    <keyword>int</keyword>
                    <keyword>long</keyword>
                    <keyword>short</keyword>
                    <keyword>signed</keyword>
                    <keyword>size_t</keyword>
                    <keyword>unsigned</keyword>
                    <keyword>void</keyword>
                </context>

                <context id="storage-class" style-ref="storage-class">
                    <keyword>auto</keyword>
                    <keyword>const</keyword>
                    <keyword>extern</keyword>
                    <keyword>inline</keyword>
                    <keyword>register</keyword>
                    <keyword>restrict</keyword>
                    <keyword>static</keyword>
                    <keyword>volatile</keyword>
                </context>

                <context id="common-defines" style-ref="common-defines">
                    <keyword>NULL</keyword>
                    <keyword>MAX</keyword>
                    <keyword>MIN</keyword>
                    <keyword>TRUE</keyword>
                    <keyword>FALSE</keyword>
                    <keyword>__LINE__</keyword>
                    <keyword>__DATA__</keyword>
                    <keyword>__FILE__</keyword>
                    <keyword>__func__</keyword>
                    <keyword>__TIME__</keyword>
                    <keyword>__STDC__</keyword>
                </context>

                <!-- C99 booleans -->
                <context id="boolean" style-ref="boolean">
                    <keyword>true</keyword>
                    <keyword>false</keyword>
                </context>

            </include>
        </context>
    </definitions>
</language>

```

Maybe I was supposed to delete some field and I didn't, I don't really know what can be the problem .... Do I need to install anything extra for gedit ? Did I messed up? =S

I appreciate any possible help.

---

