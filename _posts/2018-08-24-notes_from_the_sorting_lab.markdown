---
layout: post
title:      "Notes from the Sorting Lab"
date:       2018-08-24 22:10:01 +0000
permalink:  notes_from_the_sorting_lab
---

Just worked through a lab on sorting arrays. My passing results are below, with some notes about making my code better. 

## Example One: Returns array of integers in ascending order

```
def sort_array_asc(integers)
  integers.sort do |a, b|
    a <=> b
  end
end
``` 

I wrote this out in "long hand" for the exercise. But It would be perfectly fine to write: 

```
def sort_array_asc(array)
  array.sort
end
```

## Example Two: Returns array of integers in descending order
```
def sort_array_desc(integers)
  integers.sort do |a, b|
    b <=> a
  end
end
``` 

Once again, long-hand above. Shorter version could simply be: 

```
def sort_array_desc(array)
  array.sort.reverse
end
```

## Example Three: Sort by character length
```
def sort_array_char_count(strings)
  strings.sort do |a, b|
  a.length  <=>  b.length
  end
end
```

I noticed a few examples of incorrect code online; some people coded: 
` array.sort { |a, b| a <=> b }`
 which renders everything in alphabetical order. 
 
 ## Example Four: Swap Elements
```
def swap_elements(array)
  array[1],array[2] = array[2],array[1]
  array
end
```

This one was a bit tricky. I coded it quite literally, returning the array after simply swapping the desired elemented. Another way to do this would be: 

```
def swap_elements(array)
  switch = array.pop
  array.insert(1, switch)
end
```

Here, we could "pop" off the last element, sort it as a variable ("switch"), then insert it back into the array at the first index. 

## Example Five: Reverse
One easy way to approach this method is simply to code `array.reverse` Since I'd rather write it out in longhand for something of a challenge, I came up with the following code

```
def reverse_array(array)
  reverse=[]
i = -1
   array.each do
      reverse << array[i]
      i -= 1
    end
reverse
end
```

## Example Six: Replace the second index with $
```
def kesha_maker(strings)
  kesha = []
  i = 0
  strings.each do |word|
    word[2] = "$"
    kesha << strings[i]
    i += 1
  end
  kesha
end
```

The approach I coded above uses #each, but there's a much cleaner way to do this with `map`:

```
def kesha_maker(names)
  names.map { |name| name[2] = "$" } 
  names
end
```

## Example Seven: Select all words beginning with "a"
```
def find_a(strings)
  a_strings = []
  strings.collect do |word|
    if word.start_with?("a")
      a_strings << word
  end
end
  a_strings
end
```

Again I did a longform here. A shorter, cleaner method could employ `select`:

```
def find_a(array)
  array.select { |item| item[0] == "a" }
end
```

## Example Eight: Add "s" except for the first index 
```
def add_s(array)  array.each_with_index.collect do |item, index|
   if index != 1
     item << "s"
 end
 end
array
 end
 ```
