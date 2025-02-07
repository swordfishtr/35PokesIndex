# 35 Pokes Metagames Index

These are the metagame data files, along with miscellaneous pieces of information, that various technical projects of the 35 Pokes community depend on. Keeping them on a separate repository allows us to check for updates using the github API and download as a compressed archive rather than individual files.

Check out: [35 Pokes Browser Extension](https://github.com/swordfishtr/35PokesIndex) | Discord bot (coming soon!)

Check out also the `next` branch, where we sometimes switch to temporarily for new features.

## Repository structure

The root directory is where our projects look for specific files by name.

### gametypes.txt

Used by the discord bot to tell apart formats with significant overlap but different gametypes (singles, doubles, triples, ffa etc).

(describe others)

## Metagame data file syntax

In the past, we used JSON to represent metagame data, which consisted of just the list of allowed Pokemon. It was convenient for its accessibility to just about every programming language and anyone that might take interest in a technical project. But: it's a chore to write and modify JSON, because its syntax is so generic and strict. Se we switched to a homebrewed, specialized format at the first opportunity.

The premise is, simply, "it should be possible to paste a list of Pokemon and be done with it."

### Interpreter

Files are read line-by-line. Within a line, components end with `;` to separate them from eachother. Some components accept arbitrary input after a `:` . The interpreter will ignore all lines that start with `#` . Trailing and leading whitespace, around lines and within components, are safely ignored as well. End-of-line is interpreted the same as a `;` .

<pre>
# This is a comment in a valid snippet.

Stoutland; abilities: 4: Slush Rush;
Camerupt;  moves: +Shore Up, +Spikes, -Stealth Rock, -Hidden Power;
</pre>

### Title

The first non-comment line is the title displayed in the extension's popup, the teambuilder, and other such places. We don't use the file name for this purpose, because then sorting issues happened when I tried to do that. So now the filename is used for sorting; the title, for display. This is the only type that is expected to be in every file, in a specific place. The rest is optional and can be in any order.

### Rules

(more docs to come)
