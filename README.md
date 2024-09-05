# bash_cheat_sheet
Bash Shortcuts For Maximum Productivity

![visual cheetsheet](https://github.com/sharaths27/bash_cheat_sheet/blob/main/moving_cli.png?raw=true)


### Move cursor
<table>
<tr>
<td>Ctrl + a</td>
<td>Go to the beginning of the line (Home)</td>
</tr>
<tr>
<td>Ctrl + e</td>
<td>Go to the End of the line (End)</td>
</tr>
<tr>
<td>Alt + b</td>
<td>Back (left) one word</td>
</tr>
<tr>
<td>Alt + f</td>
<td>Forward (right) one word</td>
</tr>
<tr>
<td>Ctrl + f</td>
<td>Forward one character</td>
</tr>
<tr>
<td>Ctrl + b</td>
<td>Backward one character</td>
</tr>
<tr>
<td>Ctrl + xx</td>
<td>Toggle between the start of line and current cursor position</td>
</tr>
</table>

### Edit
<table>
<tr>
<td>Ctrl + u</td>
<td>Cut the line before the cursor position</td>
</tr>
<tr>
<td>Alt + Del</td>
<td>Delete the Word before the cursor</td>
</tr>
<tr>
<td>Alt + d</td>
<td>Delete the Word after the cursor</td>
</tr>
<tr>
<td>Ctrl + d</td>
<td>Delete character under the cursor</td>
</tr>
<tr>
<td>Ctrl + h</td>
<td>Delete character before the cursor (backspace)</td>
</tr>
<tr>
<td>Ctrl + w</td>
<td>Cut the Word before the cursor to the clipboard</td>
</tr>
<tr>
<td>Ctrl + k</td>
<td>Cut the Line after the cursor to the clipboard</td>
</tr>
<tr>
<td>Alt + t</td>
<td>Swap current word with previous</td>
</tr>
<tr>
<td>Ctrl + t</td>
<td>Swap the last two characters before the cursor (typo)</td>
</tr>
<tr>
<td>Esc + t</td>
<td>Swap the last two words before the cursor.</td>
</tr>
<tr>
<td>Ctrl + y</td>
<td>Paste the last thing to be cut (yank)</td>
</tr>
<tr>
<td>Alt + u</td>
<td>UPPER capitalize every character from the cursor to the end of the current word.</td>
</tr>
<tr>
<td>Alt + l</td>
<td>Lower the case of every character from the cursor to the end of the current word.</td>
</tr>
<tr>
<td>Alt + c</td>
<td>Capitalize the character under the cursor and move to the end of the word.</td>
</tr>
<tr>
<td>Alt + r</td>
<td>Cancel the changes and put back the line as it was in the history (revert)</td>
</tr>
<tr>
<td>Сtrl + _ </td>
<td>Undo</td>
</tr>
</table>

### History
<table>
<tr>
<td>Ctrl + r</td>
<td>Recall the last command including the specified character(s)(equivalent to : vim ~/.bash_history). </td>
</tr>
<tr>
<td>Ctrl + p</td>
<td>Previous command in history (i.e. walk back through the command history)</td>
</tr>
<tr>
<td>Ctrl + n</td>
<td>Next command in history (i.e. walk forward through the command history)</td>
</tr><tr>
<td>Ctrl + s</td>
<td>Go back to the next most recent command.</td>
</tr>
<tr>
<td>Ctrl + o</td>
<td>Execute the command found via Ctrl+r or Ctrl+s</td>
</tr>
<tr>
<td>Ctrl + g</td>
<td>Escape from history searching mode</td>
</tr>
<tr>
<td>Alt + .</td>
<td>Use the last word of the previous command</td>
</tr>
</table>

### Process control


### Bang(!) - The History Expansion
Bash also has some handy features that use the ! (bang) to allow you to do some funky stuff with bash commands.<br>
General notation is `'![event][:word[:modifier[:modifier]...]]'`.<br>
You may omit word separator `':'`, if the word designator begins with a `'^'`, `'$'`, `'*'`, `'-'`, or `'%'`.<br>
If a word designator is supplied without an event specification, the previous command is used as the event.<br>
After the optional word designator, you can add a sequence of one or more modifiers, each preceded by a `':'`.<br>

<table>
  <tr>
    <th>Events</th><th>Meaning</th><th>Example</th>
  </tr>
  <tr>
    <td>!</td>
    <td>Start a history substitution, except when followed by a space, tab, the end of the line, ‘=’ or ‘(’ (when the extglob shell option is enabled using the shopt builtin).</td>
    <td>
<pre>
</pre>
    </td>
  </tr>
  <tr>
    <td>!<i>n</i></td>
    <td>Refer to command line <i><b>n</b></i>.</td>
    <td>
<pre>
$ history
1 echo foo bar baz
2 history
$ !1
#Print command that will be saved in history
#+and executed
echo foo bar baz
#Actual execution
foo bar baz
</pre>
    </td>
  </tr>
  <tr>
    <td>!-<i>n</i></td>
    <td>Refer to the command <i><b>n</b></i> lines back.</td>
    <td>
<pre>
$ history
1 echo foo
2 echo bar
3 echo baz
4 history
$ !-3
echo bar
bar
</pre>
    </td>
  </tr>
  <tr>
    <td>!!</td>
    <td>Refer to the previous command. This is a synonym for ‘!-1’.</td>
    <td>
<pre>
$ echo foo bar baz
foo bar baz
$ !!
echo foo bar baz
foo bar baz
</pre>
    </td>
  </tr>
  <tr>
    <td>!<i>string</i></td>
    <td>Refer to the most recent command preceding the current position in the history list starting with <i><b>string</b></i>.</td>
    <td>
<pre>
$printf '%s\n' foo
foo
$ echo bar
bar
$ !pri
printf '%s\n' foo
foo
</pre>
    </td>
  </tr>
  <tr>
    <td>!?<i>string</i>[?]</td>
    <td>Refer to the most recent command preceding the current position in the history list containing <i><b>string</b></i>. The trailing ‘?’ may be omitted if the <i><b>string</b></i> is followed immediately by a newline.</td>
    <td>
<pre>
$printf '%s\n' foo
foo
$ echo bar
bar
$ !?ntf
printf '%s\n' foo
foo
$ !?bar
echo bar
bar
</pre>
    </td>
  </tr>
  <tr>
    <td>^<i>string1</i>^<i>tring2</i>^</td>
    <td>Quick Substitution. Repeat the last command, replacing <i><b>string1</b></i> with <i><b>string2</b></i>. Equivalent to `!!:s/string1/string2`.</td>
    <td>
    For more info, refer to `s/old/new/` in <b>Modifiers</b> section.
<pre>
$ echo foo
foo
$ ^echo^printf '%s\n'^
printf '%s\n' foo
foo
</pre>
    </td>
  </tr>
  <tr>
    <td>!#</td>
    <td>Repeat entire command line before this event.</td>
    <td>
<pre>
$ echo foo; echo bar; !#echo baz
echo foo; echo bar; echo foo; echo bar; echo baz
foo
bar
foo
bar
baz
</pre>
    </td>
  </tr>
  <tr>
    <th>Words</th><th>Meaning</th><th>Example</th>
  </tr>
  <tr>
    <td>0 (zero)</td>
    <td>The 0th word. For many applications, this is the command word.</td>
    <td>
<pre>
$ echo foo
foo
$ !:0
echo

</pre>
    </td>
  </tr>
  <tr>
    <td><i>n</i></td>
    <td>The <i><b>n</b></i>th word.</td>
    <td>
<pre>
$ echo foo bar baz
foo bar baz
$ echo !:2
echo bar
bar
</pre>
    </td>
  </tr>
  <tr>
    <td>^</td>
    <td>The first argument; that is, word 1.</td>
    <td>
<pre>
$ echo foo bar baz
foo bar baz
$ echo !^
echo foo
foo
</pre>
    </td>
  </tr>
  <tr>
    <td><pre>$</pre></td>
    <td>The last argument.</td>
    <td>
<pre>
$ echo foo bar baz
foo bar baz
$ echo !$
echo baz
baz
</pre>
    </td>
  </tr>
  <tr>
    <td>%</td>
    <td>The word matched by the most recent `?string?` search</td>
    <td>
<pre>
$ echo foo
foo
$ printf '%s\n' bar
bar
$ !?ch
echo foo
foo
$ !% baz
echo baz
baz
$ !?bar
printf '%s\n' bar
bar
$ echo !%
echo bar
bar
</pre>
    </td>
  </tr>
  <tr>
    <td>x-y</td>
    <td>A range of words; `-y` abbreviates `0-y`.</td>
    <td>
<pre>
$ echo foo bar baz
foo bar baz
$ echo !:2-3
echo bar baz
bar baz
$ !:-1
echo bar
bar
</pre>
    </td>
  </tr>
  <tr>
    <td>*</td>
    <td>All of the words, except the 0th. This is a synonym for `1-$`. It is not an error to use `*` if there is just one word in the event - the empty string is returned in that case.</td>
    <td>
<pre>
$ echo foo bar baz
foo bar baz
$ printf '%s\n' !*
printf '%s\n' foo bar baz
foo
bar
baz
</pre>
    </td>
  </tr>
  <tr>
    <td>x*</td>
    <td>Abbreviates `x-$`</td>
    <td>
<pre>
$ echo foo bar baz
foo bar baz
$ printf '%s\n' !:2*
printf '%s\n' bar baz
bar
baz
</pre>
    </td>
  </tr>
  <tr>
    <td>x-</td>
    <td>Abbreviates `x-$` like `x*`, but omits the last word.</td>
    <td>
<pre>
$ echo foo bar baz
foo bar baz
$ printf '%s\n' !:0-
printf '%s\n' echo foo bar
echo
foo
bar
</pre>
    </td>
  </tr>
  <tr>
    <th>Modifiers</th><th>Meaning</th><th>Example</th>
  </tr>
  <tr>
    <td>p</td>
    <td>Print the new command but do not execute it.<br>Printed command is saved in history, so you can use <kbd>Ctrl+p</kbd> to re-enter it in current prompt.</td>
    <td>
<pre>
$ echo foo bar baz
foo bar baz
$ !:p
#Printed, but not executed
echo foo bar baz
$ !:*:p
foo bar baz
</pre>
    </td>
  </tr>
  <tr>
    <td>h</td>
    <td>Remove a trailing pathname component, leaving only the head (Actually, remove all after last `/`, including).</td>
    <td>
<pre>
$ echo foo /example/path/bar.txt baz
foo /example/path/bar.txt baz
$ !:p:h
echo foo /example/path
</pre>
    </td>
  </tr>
  <tr>
    <td>t</td>
    <td>Remove all leading pathname components, leaving the tail (Actually, remove all before last `/`, including).</td>
    <td>
<pre>
$ echo foo /example/path/bar.txt baz
foo /example/path/bar.txt baz
$ !:p:t
bar.txt baz
</pre>
    </td>
  </tr>
  <tr>
    <td>r</td>
    <td>Remove a trailing suffix of the form `.suffix`, leaving the basename (Actually, remove all after last `.`, including).</td>
    <td>
<pre>
$ echo foo /example/path/bar.txt baz
foo /example/path/bar.txt baz
$ !:p:r
echo foo /example/path/bar
</pre>
    </td>
  </tr>
  <tr>
    <td>e</td>
    <td>Remove all but the trailing suffix (Actually, remove all before last `.`, including).</td>
    <td>
<pre>
$ echo foo /example/path/bar.txt baz
foo /example/path/bar.txt baz
$ !:p:e
txt baz
</pre>
    </td>
  </tr>
  <tr>
    <td>q</td>
    <td>Quote the substituted words, escaping further substitutions.</td>
    <td>
<pre>
$ echo foo 'bar baz'
foo bar baz
$ !:p:q
'echo foo '\'bar baz'\'''
</pre>
    </td>
  </tr>
  <tr>
    <td>x</td>
    <td>Quote the substituted words as with ‘q’, but break into words at spaces, tabs, and newlines.</td>
    <td>
<pre>
$ echo foo 'bar baz'
foo bar baz
$ !:p:x
'echo' 'foo' ''\'bar' 'baz'\'''
</pre>
    </td>
  </tr>
  <tr>
    <td><i>s/<i>old</i>/<i>new</i>/</i></td>
    <td>Substitute <i><b>new</b></i> for the first occurrence of <i><b>old</b></i> in the event line. Any delimiter may be used in place of `/`. The delimiter may be quoted in <i><b>old</b></i> and <i><b>new</b></i> with a single backslash. If `&` appears in <i><b>new</b></i>, it is replaced by <i><b>old</b></i>. A single backslash will quote the `&`. The final delimiter is optional if it is the last character on the input line.</td>
    <td>
<pre>
$ echo foo bar
foo bar
$ !:p:s/foo/baz
echo baz bar
</pre>
    </td>
  </tr>
  <tr>
    <td>&</td>
    <td>Repeat the previous substitution.</td>
    <td>
<pre>
$ echo foo bar
foo bar
$ !:p:s/foo/baz
echo baz bar
$ printf '%s\n' foo
foo
$ !:p:&
printf '%s\n' baz
</pre>
    </td>
  </tr>
  <tr>
    <td>g<br>a</td>
    <td>Cause changes to be applied over the entire event line. Used in conjunction with `s`, as in gs/old/new/, or with `&`.</td>
    <td>
<pre>
$ echo foo bar foo
foo bar foo
$ !:p:gs/foo/baz
echo baz bar baz
</pre>
    </td>
  </tr>
  <tr>
    <td>G</td>
    <td>Apply the following ‘s’ modifier once to each word in the event.</td>
    <td>Result is same as in `g` modifier
<pre>
</pre>
    </td>
  </tr>
</table>


####################################################################################

<p align="left"><b>Command Editing Shortcuts</b><br><br>    Ctrl + a – go to the start of the command line<br>    Ctrl + e – go to the end of the command line<br>    Ctrl + k – delete from cursor to the end of the command line<br>    Ctrl + u – delete from cursor to the start of the command line<br>    Ctrl + w – delete from cursor to start of word (i.e. delete backwards one word)<br>    Ctrl + y – paste word or text that was cut using one of the deletion shortcuts (such as the one above) after the cursor<br>    Ctrl + xx – move between start of command line and current cursor position (and back again)<br>    Alt + b – move backward one word (or go to start of word the cursor is currently on)<br>    Alt + f – move forward one word (or go to end of word the cursor is currently on)<br>    Alt + d – delete to end of word starting at cursor (whole word if cursor is at the beginning of word)<br>    Alt + c – capitalize to end of word starting at cursor (whole word if cursor is at the beginning of word)<br>    Alt + u – make uppercase from cursor to end of word<br>    Alt + l – make lowercase from cursor to end of word<br>    Alt + t – swap current word with previous<br>    Ctrl + f – move forward one character<br>    Ctrl + b – move backward one character<br>    Ctrl + d – delete character under the cursor<br>    Ctrl + h – delete character before the cursor<br>    Ctrl + t – swap character under cursor with the previous one<br><br><b>Command Recall Shortcuts</b><br><br>    Ctrl + r – search the history backwards<br>    Ctrl + g – escape from history searching mode<br>    Ctrl + p – previous command in history (i.e. walk back through the command history)<br>    Ctrl + n – next command in history (i.e. walk forward through the command history)<br>    Alt + . – use the last word of the previous command<br><br><b>Command Control Shortcuts</b>b><br><br>    Ctrl + l – clear the screen<br>    Ctrl + s – stops the output to the screen (for long running verbose command)<br>    Ctrl + q – allow output to the screen (if previously stopped using command above)<br>    Ctrl + c – terminate the command<br>    Ctrl + z – suspend/stop the command<br><br><b>Bash Bang (!) Commands</b><br><br>Bash also has some handy features that use the ! (bang) to allow you to do some funky stuff with bash commands.<br><br> <b>   !! – run last command</b><br>    !blah – run the most recent command that starts with ‘blah’ (e.g. !ls)<br>    !blah:p – print out the command that !blah would run (also adds it as the latest command in the command history)<br>    !$ – the last word of the previous command (same as Alt + .)<br>    !$:p – print out the word that !$ would substitute<br>    !* – the previous command except for the last word (e.g. if you type ‘_find somefile.txt /’, then !* would give you ‘_find somefile.txt’)<br>    !*:p – print out what !* would substitute

<p align="left"><b>Special keys: Tab, Backspace, Enter, Esc</b><br><br>    Text Terminals send characters (bytes), not key strokes.<br>    Special keys such as Tab, Backspace, Enter and Esc are encoded as control characters.<br>    Control characters are not printable, they display in the terminal as ^ and are intended to have an effect on applications.<br><br>    Ctrl+I = Tab<br>    Ctrl+J = Newline<br>    Ctrl+M = Enter<br>    Ctrl+[ = Escape</p>
