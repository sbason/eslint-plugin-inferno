# Prevent usage of isMounted (inferno/no-is-mounted)

[`isMounted` is an anti-pattern][anti-pattern], is not available when using ES6 classes, and it is on its way to being officially deprecated.

[anti-pattern]: https://facebook.github.io/inferno/blog/2015/12/16/ismounted-antipattern.html

## Rule Details

The following patterns are considered warnings:

```jsx
var Hello = Inferno.createClass({
  handleClick: function() {
    setTimeout(function() {
      if (this.isMounted()) {
        return;
      }
    });
  },
  render: function() {
    return <div onClick={this.handleClick.bind(this)}>Hello</div>;
  }
});
```

The following patterns are not considered warnings:

```jsx
var Hello = Inferno.createClass({
  render: function() {
    return <div onClick={this.props.handleClick}>Hello</div>;
  }
});
```
