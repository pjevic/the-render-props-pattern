<!-- @format -->

# The Render Props & Hiher-Order Component (HOC)

## The Render Prop Pattern

The **Render Props Pattern** allows components to share logic with others by **passing a function as a prop**. This makes components more reusable and customizable.

The `List` component in this example uses a `render` prop to delegate the rendering of each list item to the parent component. Instead of hardcoding the rendering logic, the parent provides a function to determine how each item is displayed.

### Example Usage

```jsx
<List
  title="Products"
  items={products}
  render={(product) => <ProductItem key={product.productName} product={product} />}
/>
```

### `List` Component Implementation

The `List` component is a reusable, generic component that handles the structure and behavior of a list. It uses the `render` prop to allow the parent component to customize the rendering of each item.

```jsx
function List({ title, items, render }) {
  return (
    <div>
      <p>{title}</p>
      <ul className="list">{items.map(render)}</ul>
    </div>
  );
}
```

### Advantages

- **Promotes Reuse**:  
  The `List` component can render any type of data (e.g., products, companies) because it doesn’t dictate how the items should look.

- **Customizability**:  
  The parent component has full control over how each item is rendered by passing a custom `render` function.

---

### Inversion of Control

**Inversion of Control (IoC)** occurs when a generic component like `List` does not manage the specifics of rendering or processing data itself. Instead, it delegates control to the parent component via the `render` prop.

This shifts the responsibility for how items are rendered from the `List` component to the parent.

---

## Hiher-Order Component (HOC) Pattern
