# DriftDrawer
It is a library for custom Naviagation Drawer

![Sample](images/sample.gif)

## Usage

### Gradle

```
compile 'com.sdsmdg.aridj:driftdrawer:1.0.0'
```
### Builder

1. Create a list of icons for navigation items

``` kotlin
  val icons = ArrayList<Int>()
  icons.add(R.drawable.ic_archive_black_24dp)
  icons.add(R.drawable.ic_apps_black_24dp)
  icons.add(R.drawable.ic_border_color_black_24dp)
  icons.add(R.drawable.ic_build_black_24dp)

```
2. Build the drawer programmatically using `DriftDrawerBuilder`.

``` kotlin
  DriftDrawerBuilder(context, toolbar)
    .withMenus(icons)
    .build()
```

### ItemClickListener

- Using lamdas

```kotlin
val navItemListener: (Int, View) -> Unit = { pos: Int, view: View ->
    Toast.makeText(context, "Position: " + pos, Toast.LENGTH_SHORT).show()
  }
```

- This itemClickListener can be easily pass in builder

``` kotlin
  DriftDrawerBuilder(context, toolbar)
    .withMenus(icons)
    .withItemClickListener(navItemListener)
    .build()
```

### Builder Extras

``` kotlin
val driftDrawer = DriftDrawerBuilder(this, toolbar)
    .withMenus(icons)
    .withDrawerClosed(false) // set initial state of drawer
    .withSize(60) // set menu size in dp
    .withColors(Color.parseColor("#E91E63"), Color.parseColor("#9C27B0")) // sets background and item highlight colors
    .withItemClickListener(navItemListener) // sets item click listener
    .build()
```

### DriftDrawer
`build` method of `DriftDrawerBuilder` returns `DriftDrawer`. This drawer can be used to control its behaviors.

Methods | Definition
------------ | -------------
isClosed | returns true if drawer is closed otherwise false
closeDrawer | close the drawer with/ without animation control by argument `animated`. Default value for `animated` is `true`
openDrawer | open the drawer with/ without animation control by argument `animated`. Default value for `animated` is `true`
setSelectedPosition | sets the position passed in argument as selected position
getLayout | returns the `DriftNavLayout` for drawer
