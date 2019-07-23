# cheatsheets
Notes and other cheat sheets about various programming related topics

The motivation for this repo is to collect various information I find that I keep needing while coding, starting with a solid reference for markdown syntax in particular - which is this `README.md` document.

Mostly this comes from the [commonmark](https://spec.commonmark.org/0.29/) spec.

So here are my rules about writing markdown.

  - **Soft wrap lines**
    
    To facilitate editing use one line per paragraph. Modern editors can soft wrap things easily enough. The one caveat is that it does make the document a little less readable in standard ASCII mode, but generally we are going to consider that a reasonable sacrifice in order to achieve more easily written documents
    
  - **Headings**
  
    There are two ways to do headings. The first is to use `=` and `-` underlines for H1 and H2 level headings respectively.
    
    However, since you only get 1 & 2, which typically kinds of suck, generally the preference is to use "ATX Style" which consists of 1 to 6 `#` characters at the beginning of the line followed by a space and the inline heading content. Only the beginning ones are relevant but trailing ones add visual balance thus.
    
    ### This is a H3 ###
    
    ... which is also within the existing block
    
      #### And this is an H4 ####
      
      Which really should be further indented I _think_ but am not entirely sure. Looks like this idention isn't very reliable so it is not preferred. Think **"Headings do not indent"** - which is sort of a shame :(
      
  - **Emphasis and Underlines**
  
    So while both `*` and `_` can be used to mark **bold** and _underlined_ text based on how many you use, let's prefer the `*` for bold and the underscore `_` for underlining.
    
    There is also a 3 marker ***strong emphasis*** when you want both. So 1, 2, or 3 to indicate the strength you're going for.
    
  - **Lists**
  
    Lists are kind of a primary container thing. Use a `-` to start an unordered LI and a number followed by a `.` or `)` to start an ordered list. The marker must be followed by one or more whitespace characters and then a non whitespace character. The indention level which defines an item is the colum in which the first non whitespace character after the list item marker begins in. Thus it can be as low as 1 or as high as whatever.
  
    - New list item here
      
      With continuation here under the N
      
    -    Another new list itm
    
         Which has to have content indented this far
         
      or else it's a new item (even without the marker because we're in list already)  
      
    They will define a new block on their own
    - and will interrupt the current paragraph as this shows, even without a space before them.
    They must have a space after them in order to end.
    
    Thus the list item above has ended.
    - This starts a new list
    - This is a second item
    that has a run on inline text still.
    - While this item
      
      has ended because there was a blank line, but this next paragraph is indented further than the list originally was, so it is a continuation of the list.
      
        And even those this paragraph is indented 2 spaces (because 4 would indicate code), the indention alone doesn't define a new level. Only the list actually causes a new indention level   
      - This new sub list has to use an indention that matches the paragraph that continued the block.
    - Whereas this item is back at the level above.  
    
    1. Finally, using numbers is an ordered list (here already one level down I guess)
    2. And while the list markers can be numbers followed by either `.` or `)`, changing this will
    3) Cause a reset to the creation
    4) of a new list
      
       Words
       1. Same rules
       
       
  - **Item -> Detail Lists**
    
    This seems to come up all the time! Effectively something similar to a dictionary list. This list of rules demonstrates the basic idea. Start a new ordered or un-ordered list with 2 spaces indention for the heading. For un-ordered lists use a `-` for ordered lists use `1.` style numbering which you keep up to date in the ascii file.
    
    The item being described should generally be bolded using the double `**` wrapper.
    
    Description paragraphs then will start one blank line below the item and will be indented by 4 spaces to indicate that they are continuation paragraphs for the item. If they don't have a blank line between the item and the description the are part of the same line.
    
      - **Sub rules** - 
      Continue to use the 2 character indention to move down in levels. This line shows an example that is a sub topic of the item description.
      
  - **Basic Links**
  
    [Links to urls](http://example.com) are created using the rule **HARD** then _soft_. That is, the hard corners of the `[ ]` to describe the impactful text you are putting in the document prior to the paranthetical behind the scenes nature of the rounded `( )` that hold the url. Inside the parens you an add a title as a quoted string after the url like so [for links you want to be mysterious](https://google.com "Totally not google")
    
    When you want to just inline the link, writing it generally works but using `< >` brackets around it makes it an "autolink" like so <http://example.com>
    
    Email links can be `mailto:` links <mailto:noone@nowhere.com> or just addresses <noone@nowhere.com> although this isn't supported properly in Jetbrains it seems.
    
    The link text can contain other content but not other links. [So **this** is totally legit]()  
    
  - **Reference Links**
  
    These give you a level on indirection. They let you define other "references" that you name with a "link label" which can be inserted into your narrative writing without reproducing the full url each time you mention something external. So imagine you have some links like this (You won't see the reference link definitions rendered. They are only directly visible in the source text)
    
    [google]: https://google.com  "The Goog"
    [yahoo]:  https://yahoo.com   "A bunch of yahoo's"
    
    And then you can refer to them [like this][google]       
    
    That's the full method, but there are two shortcuts. These are all equivalent
    
        [google][google]
        [google][]
        [google]
        
    So we can narratively write [google] and get the url and title from the defintion elsewhere.
    
    The definitions need the `:` following the bracketed text and a url. The title is optional and must be quoted if it is used. The link label `google` is not case sensitive. So [Google] also matches that earlier defintion.    
    
  - **Images**
    
    Images are just links that use the `<img>` tag instead of the `<a>` tag. As such they are the same, but they start with a `!` to say  "hey, this is an image man!"
    
    ![Really, an image](im-a-image.png "this is my title")
    
    The link text becomes the `alt=` text for the image. The title is basically hover text. The alt text can be empty if you hate people using screen readers.
    
    Images can also use the reference link approach so the urls could be placed all at the bottom of a document for instance and then referred to when needed like `![kittens]` ![kittens]
    
    > Assuming you have this somewhere else in the doc
    >    
    >     [kittens]: http://placekitten.com/20/20
    
    [kittens]: http://placekitten.com/20/20
    
    The other difference with image links is that their text can contain links. I think like this ![[google]](im-a-image.png)
         
  - **Horizontal Rules**
  
    These aren't all that pretty but are useful for separating sections in a document. The can be made with `-`, `_`, or `*` characters. The rules a < 4 spaces of indention followed by 3 or more of these. At 4 spaces it becomes a code block. They can happen inside other elements by maintaining the same indention as that other block like so.   
    
      * * *
    
    There should be a `<hr/>` above this paragraph but it looks like the JetBrains parser doesn't do that correctly. It does at least do a paragraph break. They don't technically need spaces above and below them but for readability it's probably worthwhile to space things out.
    
  - **Hard Breaks**
  
    A line with 2 or more spaces at the end of it followed by another line will cause a hard break (a `<br/>` tag in HTML)
    
    Without the spaces this is  
    a single line of text but the spaces after "is" cause the insertion of the `<br/>`
    
  - **Code**
  
    There is of course the `` ` `` for use as an inline code marker and the 4 space indention from the previous block level to indicate a code block. The inline marker is actually **one or more** backticks so you can see how the single backtick was included above.
        
        Code here
        
    Those 4 space indented blocks need blank lines before and after them.
    
    Then there is the 3rd method of using a code fence which is 3 ` or ~ characters at the block level of indention like so.
    
    ``` javascript
    Here is some code which is fenced by the 3 ``` characters above 
    and below it.
    ```
     
    Following the first code fence marker a programming language can be added but is not required.
    
    There is also a form of the inline code where you use only two backticks and then it's not a block. ``
    It's just some
    inline code with the
    whitespaces not honored.
    `` 
    
    That form is potentially interesting when you have ``a long url that will wrap around
    to the next line but you don't want that newline included``
    Although honestly it doesn't seem required even for that.
    
  - **Block Quotes**
  
    These begin with a `>` character in the first paragraph character location like so
    
    > This is block quoted
    
    >This is a second block
    
    > But they can also be
    continued text
    without a break
    >
    > And if you need multiple paragraphs you probably need to use > at the beginning of each line.
    
    These are good for "hey pay attention to this note!" sort of information.
    
  - **HTML**
  
    There are 7 ways(!) to include HTML in markdown if the parser is going to support it. The basic thing is just write it <i>into the code</i> like you would if writing an HTML page, including adding `<script>` tags. This seems problematic and maybe not good, but might be useful to put fun hacks onto a page on github in particular.
    
  
## Examples

There should be a "thematic break" - AKA a `<hr/>` after this

* * *

And also after this

- - -

And this one
______________________



##### Lists #####

1. First
   1. It takes 3 spaces to get to a sub list
   2. Lorem
  2. yeah, even 2 spaces is still at the first level
  
  
- First
  - Only 2 spaces for an unordered though!!!!
   - Three is still before
    - As is 4 (I think we're counting from 2 in right now)
     - So 5 indents is only 2+3 - not yet code
      - But now we are code???
      
      Weired
      
      Hah!
      
      Okay
      
      